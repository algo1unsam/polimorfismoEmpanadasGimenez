# Empanadas Giménez

<img src="img/empanadasGimenez.png" height="200" width="300">

## Planteo inicial

En "Empanadas Giménez", un modesto local de delivery de empanadas, tenemos dos empleados:

* Galván, el empleado de siempre, que cobra un sueldo fijo. El valor arranca en $ 15.000, y después puede cambiar mes a mes.
* Baigorria, el joven y explotado empleado de Giménez, que cobra en base a la cantidad de empanadas vendidas (actualmente $ 15 por empanada).

El dueño, el señor Giménez, es el encargado de pagarle el sueldo a los empleados, y de gestionar el dinero que se utiliza para esto. Asumimos que Giménez arranca con un fondo para sueldos de $ 300.000. Como los sueldos salen de este fondo, hay que descontar el importe correspondiente cuando Giménez le paga a un empleado.

#### Hacer que Giménez le pueda pagar a un empleado cualquiera
Por ahora no vamos a tener en cuenta qué hace cada empleado al recibir el dinero, el único efecto que nos interesa del pago es que disminuye el fondo de Giménez según el sueldo del empleado.


<br>

## Qué hacen los empleados con lo que cobran

Ahora queremos agregar información de qué hacen los empleados cuando cobran el sueldo. Sabemos que:
- Baigorria cuando cobra el sueldo lo suma a un acumulador de todo lo que cobró, agregarle la capacidad de entender el mensaje `totalCobrado()`. 
- Galván no hace nada.


<br>

## Manejo fino de las finanzas de Galván

Modificar el comportamiento de Galván para que maneje sus gastos, el dinero que tiene, y su deuda. Cuando Galván gasta, se descuenta de su dinero, si no le alcanza aumenta la deuda. Cuando cobra un sueldo, Galván paga sus deudas. Si sobra algo, se suma al dinero que tiene. Agregar a Galván la capacidad de entender los mensajes: `gastar(cuanto)`, `totalDeuda()`, `totalDinero()`.

## Testear los siguientes escenarios
1. Galván arranca con deuda en 0 y dinero en 0. Su sueldo (que aún no cobró) es de 15000.
2. Si Galván gasta 4000, `totalDeuda()` debe ser 4000, `totalDinero()` debe ser 0.
3. Si Galván gasta primero 2000 y luego 5000, la deuda se suma. `totalDeuda()` pasa a 7000, `totalDinero()` sigue en 0.
4. Si Galván hasta 8000 y luego cobra, con los 15000 que recibe paga toda su deuda y le sobran 7000 pesos. Por lo tanto, `totalDeuda()` debe ser 0, y `totalDinero()` debe ser 7000.
5. Si Galván gasta 20000 y luego cobra, tiene que dedicar los 15000 a pagar deudas, y no le alcanza. Ahora, `totalDeuda()` pasa a 5000, y `totalDinero()` a 0.
6. Si Galván cobra y luego gasta 25000, cubre 15000 con el dinero que tiene, el resto es deuda. `totalDeuda()` queda en 10000, `totalDinero()` en 0.

<br>

# Conceptos vistos en el ejemplo

* Modelar objetos
* Polimorfismo entre Baigorria y Galván.
  * Para pensar: ¿quién se aprovecha de ese polimorfismo? ¿qué mensaje está involucrado?
* Testing
