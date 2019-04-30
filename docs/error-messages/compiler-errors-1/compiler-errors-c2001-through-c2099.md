---
title: Errores del compilador de C2000 a C2099
ms.date: 04/21/2019
f1_keywords:
- C2000
- C2016
- C2023
- C2024
- C2025
- C2029
- C2031
- C2035
- C2037
- C2038
- C2049
- C2068
- C2076
- C2080
- C2096
- C2098
helpviewer_keywords:
- C2000
- C2016
- C2023
- C2024
- C2025
- C2029
- C2031
- C2035
- C2037
- C2038
- C2049
- C2068
- C2076
- C2080
- C2096
- C2098
ms.assetid: d99a19eb-eeeb-4181-9b33-9cbe4459767b
ms.openlocfilehash: cf1d2f647c13b589463624749e29dc277f6f1d3e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62360494"
---
# <a name="compiler-errors-c2000-through-c2099"></a>Errores del compilador de C2000 a C2099

Los artículos de esta sección de la documentación explican un subconjunto de los mensajes de error generados por el compilador.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Mensajes de error

|Error|Mensaje|
|-----------|-------------|
|Error del compilador de C2000|ERROR DESCONOCIDO Elija el comando soporte técnico en el menú Ayuda de Visual C++, o abra el archivo de Ayuda de soporte técnico para obtener más información|
|[Error del compilador C2001](compiler-error-c2001.md)|nueva línea en constante|
|[Error del compilador C2002](compiler-error-c2002.md)|constante de caracteres anchos no válida|
|[Error del compilador C2003](compiler-error-c2003.md)|se esperaba 'defined id'|
|[Error del compilador C2004](compiler-error-c2004.md)|se esperaba 'defined(id)'|
|[Error del compilador C2005](compiler-error-c2005.md)|#line esperaba un número de línea, se encontró '*token*'|
|[Error del compilador C2006](compiler-error-c2006.md)|'*directiva*': se esperaba un nombre de archivo, se encontró '*token*'|
|[Error del compilador C2007](compiler-error-c2007.md)|#define sintaxis|
|[Error del compilador C2008](compiler-error-c2008.md)|'*carácter*': no se esperaba en la definición de macro|
|[Error del compilador C2009](compiler-error-c2009.md)|reutilización de formal de macro '*identificador*'|
|[Error del compilador C2010](compiler-error-c2010.md)|'*carácter*': no se esperaba en la lista de parámetros formales de macro|
|[Error del compilador C2011](compiler-error-c2011.md)|'*identificador*': '*tipo*' nueva definición del tipo|
|[Error del compilador C2012](compiler-error-c2012.md)|Falta un nombre detrás ' <'|
|[Error del compilador C2013](compiler-error-c2013.md)|falta '>'|
|[Error del compilador C2014](compiler-error-c2014.md)|comando de preprocesador debe empezar con un primer espacio|
|[Error del compilador C2015](compiler-error-c2015.md)|demasiados caracteres en la constante|
|Error del compilador C2016|C requiere que un struct o union tenga al menos un miembro|
|[Error del compilador C2017](compiler-error-c2017.md)|secuencia de escape no válida|
|[Error del compilador C2018](compiler-error-c2018.md)|carácter desconocido ' 0 x*valor*'|
|[Error del compilador C2019](compiler-error-c2019.md)|se encontró la directiva de preprocesador esperada, '*carácter*'|
|[Error del compilador C2020](compiler-error-c2020.md)|'*miembro*': '*clase*' nueva definición de miembro|
|[Error del compilador C2021](compiler-error-c2021.md)|se esperaba un valor de exponente, no '*carácter*'|
|[Error del compilador C2022](compiler-error-c2022.md)|'*número*': demasiado grande para el carácter|
|Error del compilador C2023|'*identificador*': Alineación (*Número1*) difiere de la declaración anterior (*número2*)|
|Error del compilador C2024|el atributo 'alignas' se aplica a las variables, los miembros de datos y solo los tipos de etiquetas|
|Error del compilador C2025|archivo de interfaz de módulo binario no válido o dañado: '*filename*'|
|[Error del compilador C2026](compiler-error-c2026.md)|cadena demasiado grande, caracteres finales truncados|
|[Error del compilador C2027](compiler-error-c2027.md)|el uso de un tipo no definido '*tipo*'|
|[Error del compilador C2028](compiler-error-c2028.md)|el miembro struct/union debe estar dentro de una estructura o unión|
|Error del compilador C2029|operando izquierdo de '*token*'especifica la clase/struct/interface sin definir'*identificador*'|
|[Error del compilador C2030](compiler-error-c2030.md)|un destructor con accesibilidad 'protected private' no puede ser miembro de una clase declarada 'sealed'|
|Error del compilador C2031|un destructor virtual con '*accesibilidad*' para este tipo no se permite la accesibilidad|
|[Error del compilador C2032](compiler-error-c2032.md)|'*identificador*': función no puede ser miembro del struct/union '*tipo*'|
|[Error del compilador C2033](compiler-error-c2033.md)|'*identificador*': campo de bits no puede tener direccionamiento indirecto|
|[Error del compilador C2034](compiler-error-c2034.md)|'*identificador*': tipo de campo de bits demasiado pequeño para el número de bits|
|Error del compilador C2035|un destructor no virtual con '*accesibilidad*' para este tipo no se permite la accesibilidad|
|[Error del compilador C2036](compiler-error-c2036.md)|'*identificador*': tamaño desconocido|
|Error del compilador C2037|operando izquierdo de '*identificador*'especifica struct/union sin definir'*tipo*'|
|Error del compilador C2038|el espacio de nombres std no puede estar en línea|
|[Error del compilador C2039](compiler-error-c2039.md)|'*identificador1*': no es un miembro de '*identificador2*'|
|[Error del compilador C2040](compiler-error-c2040.md)|'*operador*': '*identificador1*'se diferencia en los niveles de direccionamiento indirecto de'*identificador2*'|
|[Error del compilador C2041](compiler-error-c2041.md)|dígitos no válido '*carácter*'para la base'*número*'|
|[Error del compilador C2042](compiler-error-c2042.md)|las palabras clave signed/unsigned se excluyen mutuamente|
|[Error del compilador C2043](compiler-error-c2043.md)|instrucción break no válida|
|[Error del compilador C2044](compiler-error-c2044.md)|instrucción continue no válida|
|[Error del compilador C2045](compiler-error-c2045.md)|'*identificador*': etiqueta redefinida|
|[Error del compilador C2046](compiler-error-c2046.md)|palabra clave case no válida|
|[Error del compilador C2047](compiler-error-c2047.md)|palabra clave default no válida|
|[Error del compilador C2048](compiler-error-c2048.md)|más de una etiqueta default|
|Error del compilador C2049|'*identificador*': espacio de nombres no insertado no se puede abrir como en línea|
|[Error del compilador C2050](compiler-error-c2050.md)|expresión switch no integral|
|[Error del compilador C2051](compiler-error-c2051.md)|expresión case no constante|
|[Error del compilador C2052](compiler-error-c2052.md)|'*tipo*': tipo no válido para la expresión case|
|[Error del compilador C2053](compiler-error-c2053.md)|'*identificador*': cadena de caracteres anchos|
|[Error del compilador C2054](compiler-error-c2054.md)|se esperaba ' (' seguir '*identificador*'|
|[Error del compilador C2055](compiler-error-c2055.md)|lista de parámetros formales, no una lista de tipos de espera|
|[Error del compilador C2056](compiler-error-c2056.md)|expresión no válida|
|[Error del compilador C2057](compiler-error-c2057.md)|se esperaba una expresión constante|
|[Error del compilador C2058](compiler-error-c2058.md)|la expresión constante no es de tipo integral|
|[Error del compilador C2059](compiler-error-c2059.md)|error de sintaxis: '*token*'|
|[Error del compilador C2060](compiler-error-c2060.md)|error de sintaxis: se encontró el final del archivo|
|[Error del compilador C2061](compiler-error-c2061.md)|error de sintaxis: identificador '*identificador*'|
|[Error del compilador C2062](compiler-error-c2062.md)|tipo de '*tipo*' inesperado|
|[Error del compilador C2063](compiler-error-c2063.md)|'*identificador*': no es una función|
|[Error del compilador error C2064](compiler-error-c2064.md)|término no se evalúa como una toma de la función *número* argumentos|
|[Error del compilador C2065](compiler-error-c2065.md)|'*identificador*': identificador no declarado|
|[Error del compilador C2066](compiler-error-c2066.md)|la conversión al tipo de función no es válida|
|[Error del compilador C2067](compiler-error-c2067.md)|la conversión a tipo de matriz no es válida|
|Error del compilador C2068|uso no válido de la función sobrecargada. ¿Falta la lista de argumentos?|
|[Error del compilador C2069](compiler-error-c2069.md)|conversión del término 'void' a otro que no sea de tipo 'void'|
|[Error del compilador C2070](compiler-error-c2070.md)|'*type*': illegal sizeof operand|
|[Error del compilador C2071](compiler-error-c2071.md)|'*identificador*': clase de almacenamiento no válida|
|[Error del compilador C2072](compiler-error-c2072.md)|'*identificador*': inicialización de una función|
|[Error del compilador C2073](compiler-error-c2073.md)|'*identificador*': elementos de la matriz inicializada parcialmente deben tener un constructor predeterminado|
|[Error del compilador C2074](compiler-error-c2074.md)|'*identificador*': '*tipo*' inicialización requiere una lista de inicializadores entre llaves|
|[Error del compilador C2075](compiler-error-c2075.md)|'*identificador*': inicialización de matriz requiere una lista de inicializadores entre llaves|
|Error del compilador C2076|no se puede usar una lista de inicializadores entre llaves en una expresión nueva cuyo tipo contiene '*tipo*'|
|[Error del compilador C2077](compiler-error-c2077.md)|inicializador de campo no escalar '*identificador*'|
|[Error del compilador error C2078](compiler-error-c2078.md)|hay demasiados inicializadores|
|[Error del compilador C2079](compiler-error-c2079.md)|'*identificador*'utiliza indefinido class/struct/union'*tipo*'|
|Error del compilador C2080|'*identificador*': el tipo para '*tipo*' solo se puede deducir a partir de una expresión de inicializador simple|
|[Error del compilador C2081](compiler-error-c2081.md)|'*identificador*': nombre de no es válido de lista de parámetros formales|
|[Error del compilador C2082](compiler-error-c2082.md)|¡¡¡Redefinición del parámetro formal '*identificador*'|
|[Error del compilador C2083](compiler-error-c2083.md)|comparación struct/union no válida|
|[Error del compilador C2084](compiler-error-c2084.md)|función '*identificador*' ya tiene un cuerpo|
|[Error del compilador C2085](compiler-error-c2085.md)|'*identificador*': no en la lista de parámetros formales|
|[Error del compilador C2086](compiler-error-c2086.md)|'*identificador*': nueva definición|
|[Error del compilador C2087](compiler-error-c2087.md)|'*identificador*': falta el subíndice|
|[Error del compilador C2088](compiler-error-c2088.md)|'*operador*': no válido para la clase/struct/union|
|[Error del compilador C2089](compiler-error-c2089.md)|'*identificador*': '*tipo*' demasiado grande|
|[Error del compilador C2090](compiler-error-c2090.md)|Devuelve una matriz (función)|
|[Error del compilador C2091](compiler-error-c2091.md)|función devuelve una función|
|[Error del compilador C2092](compiler-error-c2092.md)|'*identificador*' tipo de elemento de matriz no puede ser una función|
|[Error del compilador C2093](compiler-error-c2093.md)|'*identificador1*': no se puede inicializar utilizando la dirección de la variable automática '*identificador2*'|
|[Error del compilador C2094](compiler-error-c2094.md)|etiqueta '*identificador*' no estaba definida|
|[Error del compilador C2095](compiler-error-c2095.md)|'*función*': parámetro real es de tipo 'void': parámetro *número*|
|Error del compilador C2096|'*identificador*': No se puede inicializar un miembro de datos con un inicializador entre paréntesis|
|[Error del compilador C2097](compiler-error-c2097.md)|inicialización no válida|
|Error del compilador C2098|token inesperado después del miembro de datos '*identificador*'|
|[Error del compilador C2099](compiler-error-c2099.md)|el inicializador no es una constante|

## <a name="see-also"></a>Vea también

[C /C++ herramientas errores y advertencias de compilación y el compilador](../compiler-errors-1/c-cpp-build-errors.md) \
[Errores del compilador de C2000 - C3999](../compiler-errors-1/compiler-errors-c2000-c3999.md)
