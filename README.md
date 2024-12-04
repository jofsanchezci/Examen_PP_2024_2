
# Ejercicio: Implementación de un Polinomio de Taylor para la Función Seno

## **Descripción del Problema**

Implemente una función en Python llamada `polinomio_taylor_seno(x, n)` que calcule la aproximación de la función seno en un punto \( x \) utilizando el polinomio de Taylor de grado \( n \) centrado en \( x = 0 \).

La fórmula para calcular el polinomio de Taylor de la función seno es:

$\[sin(x) \approx \sum_{k=0}^{n} (-1)^k \frac{x^{2k+1}}{(2k+1)!}\]$

Donde:
- \( (-1)^k \): alterna el signo entre positivo y negativo.
- \( x^{2k+1} \): es la potencia impar del valor \( x \).
- \( (2k+1)! \): es el factorial del exponente.

---

## **Requisitos**

1. La función debe llamarse **`polinomio_taylor_seno(x, n)`** y recibir dos parámetros:
   - `x`: un número flotante que representa el valor en el cual se evalúa el polinomio.
   - `n`: un entero positivo que indica el número de términos del polinomio de Taylor a considerar.

2. Debe incluir una función auxiliar llamada `factorial(n)` que calcule el factorial de un número entero \( n \) de manera iterativa.

3. **No se permite el uso de librerías externas** como `math` o `numpy`.

---

## **Casos de Prueba Públicos**

Los siguientes casos de prueba son públicos y servirán como referencia para evaluar el correcto funcionamiento de su implementación:

1. **Entrada:** `polinomio_taylor_seno(0, 5)`  
   **Salida Esperada:** `0.0`

2. **Entrada:** `polinomio_taylor_seno(1, 10)`  
   **Salida Esperada:** `0.8414709848078965`

3. **Entrada:** `polinomio_taylor_seno(-1, 7)`  
   **Salida Esperada:** `-0.8414709848078965`

4. **Entrada:** `polinomio_taylor_seno(3.14159, 15)`  
   **Salida Esperada:** `0.0000026535897933527` (Aproximadamente cercano a cero, considerando \( \sin(\pi) = 0 \)).

---

## **Casos de Prueba Ocultos**

Además de los casos públicos, su función será evaluada con casos ocultos para verificar:
1. Manejo de valores grandes de \( x \) y \( n \) para comprobar el rendimiento.
2. Precisión en valores cercanos a cero.
3. Comportamiento con valores negativos de \( x \).

---

## **Entrega**

Suba un archivo `.py` con su implementación. Su código será evaluado automáticamente contra los casos de prueba públicos y ocultos.

---

## **Evaluación**

1. **Correctitud:** Se verificará que la función produzca resultados correctos comparados con los valores de referencia.
2. **Eficiencia:** Se evaluará que la función maneje correctamente cálculos grandes sin problemas de rendimiento o precisión.
3. **Buena práctica:** Se valorará el uso de código claro y bien estructurado, con comentarios que expliquen las partes importantes.

---

## **Ejemplo de Implementación**

```python
def polinomio_taylor_seno(x, n):
    resultado = 0
    signo = 1
    for k in range(n):
        termino = signo * (x**(2*k + 1)) / factorial(2*k + 1)
        resultado += termino
        signo *= -1
    return resultado

def factorial(n):
    resultado = 1
    for i in range(1, n + 1):
        resultado *= i
    return resultado
```

Pruebe la implementación con los casos de prueba proporcionados para verificar su funcionalidad.

---

¡Buena suerte con tu ejercicio!
