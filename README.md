
# Ejercicio: Implementación de un Polinomio de Taylor para la Función Seno

## **Descripción del Problema**

Implemente una función en Python llamada `polinomio_taylor_seno(x, n)` que calcule la aproximación de la función seno en un punto \( x \) utilizando el polinomio de Taylor de grado \( n \) centrado en \( x = 0 \).

La fórmula para calcular el polinomio de Taylor de la función seno es:

$\[sin(x)\approx\sum_{k=0}^{n} (-1)^k \frac{x^{2k+1}}{(2k+1)!}\]$

Donde:
- $\((-1)^k \)$: alterna el signo entre positivo y negativo.
- $\(x^{2k+1} \)$: es la potencia impar del valor \( x \).
- $\((2k+1)!\)$: es el factorial del exponente.

## **Tiempo de solución 60 minutos**
---

## **Requisitos**

1. La función debe llamarse **`polinomio_taylor_seno(x, n)`** y recibir dos parámetros:
   - `x`: un número flotante que representa el valor en el cual se evalúa el polinomio.
   - `n`: un entero positivo que indica el número de términos del polinomio de Taylor a considerar.

2. Debe incluir una función auxiliar llamada `factorial(n)` que calcule el factorial de un número entero $\(n\)$ de manera iterativa.

3. **No se permite el uso de librerías externas** como `math` o `numpy`.

---

## **Casos de Prueba**

Los siguientes casos de prueba son públicos y servirán como referencia para evaluar el correcto funcionamiento de su implementación:

1. **Entrada:** `polinomio_taylor_seno(0, 5)`  
   **Salida Esperada:** `0.0`

2. **Entrada:** `polinomio_taylor_seno(1, 10)`  
   **Salida Esperada:** `0.8414709848078965`

3. **Entrada:** `polinomio_taylor_seno(-1, 7)`  
   **Salida Esperada:** `-0.8414709848078965`

4. **Entrada:** `polinomio_taylor_seno(3.14159, 15)`  
   **Salida Esperada:** `0.0000026535897933527` 
   **Aproximadamente cercano a cero, considerando $\sin(\pi\)=0\$.

---

## **Casos de Prueba Ocultos**

Además de los casos públicos, su función será evaluada con casos ocultos para verificar:
1. Manejo de valores grandes de $\(x\)$ y $\(n\)$ para comprobar el rendimiento.
2. Precisión en valores cercanos a cero.
3. Comportamiento con valores negativos de $\(x\)$.

---

## **Entrega**

Suba un archivo `.py` con su implementación. Su código será evaluado automáticamente contra los casos de prueba públicos y ocultos.

---

## **Evaluación**

1. **Correctitud:** Se verificará que la función produzca resultados correctos comparados con los valores de referencia.
2. **Eficiencia:** Se evaluará que la función maneje correctamente cálculos grandes sin problemas de rendimiento o precisión.
3. **Buena práctica:** Se valorará el uso de código claro y bien estructurado, con comentarios que expliquen las partes importantes.

---
Pruebe la implementación con los casos de prueba proporcionados para verificar su funcionalidad.

---

# Guía para la Implementación del Polinomio de Taylor para Seno

## **Aspectos a Tener en Cuenta**

### **1. Correctitud Matemática**
- **Orden de la serie**: La función debe sumar exactamente $\(n\)$ términos del polinomio de Taylor, donde $\(n\)$ es el número de términos especificado por el usuario.
- **Fórmula**: Asegúrate de implementar la fórmula correctamente:
  $\[\sin(x) \approx \sum_{k=0}^{n} (-1)^k \frac{x^{2k+1}}{(2k+1)!}\]$
  - $\((-1)^k\)$: Alterna el signo del término.
  - $\( x^{2k+1}\)$: Potencia impar de \( x \).
  - $\( (2k+1)! \)$: Factorial del exponente.

- **Exactitud**:
  - Asegúrate de que el cálculo sea lo más preciso posible, especialmente para valores pequeños o grandes de $\(x\)$.

---

### **2. Eficiencia Computacional**
- **Cálculo de Potencias y Factoriales**:
  - Usa variables acumulativas para evitar calcular potencias y factoriales desde cero en cada iteración.
    Ejemplo:
    - Para calcular $\( x^{2k+1}\)$, reutiliza el valor de la potencia anterior multiplicándolo por $\(x^2\)$.
    - Para calcular $\((2k+1)!\)$, reutiliza el valor del factorial anterior multiplicándolo por el nuevo factor.

  **Optimización del cálculo del término:**
  ```python
  potencia = x  # Inicialmente x^1
  factorial = 1  # Inicialmente 1!
  for k in range(n):
      termino = signo * potencia / factorial
      potencia *= x * x  # Incrementa a la siguiente potencia impar
      factorial *= (2*k + 2) * (2*k + 3)  # Incrementa al siguiente factorial impar
  ```
---

### **3. Manejo de Errores**
- **Validaciones de Entrada**:
  - Verifica que el número de términos $\(n\)$ sea un entero positivo.
  - Asegúrate de que $\(x\)$ sea un número válido (puede ser negativo, cero o positivo).
  
- **Errores numéricos**:
  - Evita problemas de desbordamiento (overflow) para valores grandes de $\(x\)$ o $\(n\)$ controlando el rango de entrada.
  - Para valores de $\(x\)$ mayores que $\(2\pi\)$, considera la periodicidad de la función seno:
    $\[\sin(x) = \sin(x \, \text{mod} \, 2\pi)\]$

---

### **4. Simplicidad del Código**
- Mantén el código limpio y fácil de entender:
  - Usa nombres descriptivos para las variables (ejemplo: `factorial`, `potencia`).
  - Documenta cada parte del código con comentarios claros.

Ejemplo:
```python
def polinomio_taylor_seno(x, n):
    """
    Calcula el polinomio de Taylor para seno centrado en x=0.
    
    Args:
        x (float): El valor en el cual se evalúa el seno.
        n (int): Número de términos del polinomio de Taylor.
    
    Returns:
        float: Aproximación del seno de x.
    """
    # Implementación aquí
```

---

### **5. Manejo de Casos Especiales**
- **$\(x=0\)$**: El resultado debe ser exactamente 0, sin importar el valor de $\(n\)$.
- **$\(n=1\)$**: Solo calcula el primer término de la serie.
- **Valores extremos**: Asegúrate de manejar valores grandes o pequeños de $\(x\)$ con suficiente precisión.

---

### **6. Estandarización y Buenas Prácticas**
- **Conformidad con PEP 8** (en Python):
  - Usa indentación de 4 espacios.
  - Escribe funciones pequeñas y reutilizables.
- **Pruebas**:
  - Crea casos de prueba con valores conocidos, comparando los resultados con los de una librería estándar como `math.sin`.

---

### **7. Consideraciones de Rendimiento**
- **Tolerancia de error**:
  - Ajusta el número de términos $\(n\)$ en función del error tolerado. Por ejemplo, puedes permitir una precisión específica (e.g., $\(10^{-6} \)$) y detener el cálculo cuando el término sea menor que este umbral.

---



¡Buena suerte con el ejercicio!
