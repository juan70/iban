# iban
Calcular el código IBAN de una cuenta bancaria.

(Sorry, this README is in Spanish only...)

Una página muy simple en HTML con un pequeño formulario y un poco de Javascript para hacer el cálculo.
Como hay que trabajar con números muy grandes, he echado mano de la versión pequeña de una biblioteca para hacer cálculos con números grandes: https://github.com/MikeMcl/big.js/

## Algoritmo
Según he podido leer por ahí, concretamente aquí http://www.calculariban.com/CalculoIBAN/CalculoIBAN.html, el algoritmo es el siguiente:

  1. Primero, se considera el alfabeto dándole un número de 10 a 35 a cada letra: A=10, B=11, ..., Y=34, Z=35 (no se toma en cuenta la letra Ñ).
  2. Se toma el número de cuenta con formato 1111 2222 33 4444444444 (4, 4, 2, y 10 cifras) y se le añade el código del país (ES para España, por ejemplo), y 00. Se obtiene 11112222334444444444ES00.
  3. Se reemplazan las letras del país por los números correspondientes del alfabeto del punto 1. En nuestro ejemplo: E=14 y S=28. Obtenemos: 11112222334444444444142800.
  4. Se calcula: 98 - (11112222334444444444142800 módulo 97). En este ejemplo, se obtiene 71. Si se obtuviera un número menos que 10, habría que formatearlo con 2 dígitos.
  5. Finalmente, el código IBAN de nuestro ejemplo es ES71 1111 2222 3344 4444 4444

## Por hacer
 - HECHO: Formatear a 2 dígitos si el cálculo da un número menor que 10.
