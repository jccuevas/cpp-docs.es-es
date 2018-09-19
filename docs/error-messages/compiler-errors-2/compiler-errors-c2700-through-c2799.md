---
title: C2700 de errores del compilador a C2799 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/17/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2716
- C2717
- C2727
- C2729
- C2737
- C2740
- C2741
- C2742
- C2744
- C2746
- C2747
- C2759
- C2763
- C2769
- C2772
- C2789
- C2796
- C2799
helpviewer_keywords:
- C2716
- C2717
- C2727
- C2729
- C2737
- C2740
- C2741
- C2742
- C2744
- C2746
- C2747
- C2759
- C2763
- C2769
- C2772
- C2789
- C2796
- C2799
dev_langs:
- C++
ms.assetid: 6ee257bb-94bc-42b9-af2c-3c73926afba4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8cab784c772b8b0faac2bca2bdc3ff7a3465b551
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33283863"
---
# <a name="compiler-errors-c2700-through-c2799"></a>C2700 de errores del compilador a C2799

Los artículos de esta sección de la documentación explican un subconjunto de los mensajes de error generados por el compilador.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Mensajes de error

|Error|Mensaje|
|-----------|-------------|
|[Error del compilador C2700](compiler-error-c2700.md)|'*tipo*': no se puede iniciar (utilice/W4 para obtener más información)|
|[Error del compilador C2701](compiler-error-c2701.md)|'*función*': una plantilla de función/generic no puede ser una función friend de una clase local|
|[Error del compilador C2702](compiler-error-c2702.md)| __except no puede aparecer en el bloque de finalización|
|[Error del compilador C2703](compiler-error-c2703.md)|instrucción __leave no válida|
|[Error del compilador C2704](compiler-error-c2704.md)|'*función*': __va_start intrínseco sólo se permite en varargs|
|[Error del compilador C2705](compiler-error-c2705.md)|'*etiqueta*': salto no válido en '*exception_block*' ámbito|
|[Error del compilador C2706](compiler-error-c2706.md)|__except no válido sin el correspondiente _try (falta '}' en el bloque __try?)|
|[Error del compilador C2707](compiler-error-c2707.md)|'*identificador*': contexto incorrecto para la función intrínseca|
|[Error del compilador C2708](compiler-error-c2708.md)|'*identificador*': longitud de parámetros reales en bytes es distinta respecto llamada anterior o referencia|
|[Error del compilador C2709](compiler-error-c2709.md)|'*identificador*': longitud de parámetros formales en bytes es distinta respecto declaración anterior.|
|[Error del compilador C2710](compiler-error-c2710.md)|'*identificador*': ' __declspec (*modificador*)' solo se puede aplicar a una función que devuelve un puntero|
|[Error del compilador C2711](compiler-error-c2711.md)|'*función*': esta función no se puede compilar como administrada, considere la posibilidad de usar #pragma no administrado|
|[Error del compilador C2712](compiler-error-c2712.md)|No se puede usar __try en funciones que requieran desenredo de objetos|
|[Error del compilador C2713](compiler-error-c2713.md)|un único formato de control de excepciones permitidas por función|
|[Error del compilador C2714](compiler-error-c2714.md)|no se permite alignof(void)|
|[Error del compilador C2715](compiler-error-c2715.md)|'*tipo*': no se puede producir o detectar este tipo|
|C2716 de Error del compilador|Obsoleto.|
|C2717 de Error del compilador|Obsoleto.|
|[Error del compilador C2718](compiler-error-c2718.md)|'*tipo*': el parámetro real con alineación solicitada de *número* no se alineará|
|[Error del compilador C2719](compiler-error-c2719.md)|'*parámetro*': parámetro formal con alineación solicitada de *número* no se alineará|
|[Error del compilador C2720](compiler-error-c2720.md)|'*identificador*': '*especificador*' especificador de clase de almacenamiento no es válido para miembros|
|[Error del compilador C2721](compiler-error-c2721.md)|'*especificador*': especificador de clase de almacenamiento no es válido entre la palabra clave del operador y el tipo|
|[Error del compilador C2722](compiler-error-c2722.md)|'::*operador*': comando no válido de operador siguiente; utilice ' operador *operador*'|
|[Error del compilador C2723](compiler-error-c2723.md)|'*función*': '*especificador*' especificador no es válido en la definición de función|
|[Error del compilador C2724](compiler-error-c2724.md)|'*función*': 'static' no se debe utilizar en funciones miembro definidas en el ámbito de archivo|
|[Error del compilador C2725](compiler-error-c2725.md)|'*tipo*': no se puede producir o detectar un objeto administrado o WinRT por valor o referencia|
|[Error del compilador C2726](compiler-error-c2726.md)|'gcnew' solo puede usarse para crear un objeto con tipo administrado o WinRT|
|Error C2727: Error de compilador|Obsoleto.|
|[Error del compilador C2728](compiler-error-c2728.md)|'*tipo*': una matriz nativa no puede contener este tipo|
|C2729 de Error del compilador|Obsoleto.|
|[Error del compilador C2730](compiler-error-c2730.md)|'*clase*': no puede ser una clase base de sí mismo|
|[Error del compilador C2731](compiler-error-c2731.md)|'*función*': no se pueden sobrecargar (función)|
|[Error del compilador C2732](compiler-error-c2732.md)|especificación de vinculación se contradice con la especificación anterior para '*función*'|
|[Error del compilador C2733](compiler-error-c2733.md)|'*función*': segunda vinculación C de la función sobrecargada no permitida|
|[Error del compilador C2734](compiler-error-c2734.md)|'*identificador*': objeto 'const' debe inicializarse si no 'extern'|
|[Error del compilador C2735](compiler-error-c2735.md)|'*palabra clave*' palabra clave no está permitida en el especificador de tipo de parámetros formales|
|[Error del compilador C2736](compiler-error-c2736.md)|'*palabra clave*' no se permite la palabra clave de conversión|
|C2737 de Error del compilador|'*identificador*': se debe inicializar el objeto 'constexpr'|
|[Error del compilador C2738](compiler-error-c2738.md)|' operador *tipo*': es ambiguo o no es un miembro de '*clase*'|
|[Error del compilador C2739](compiler-error-c2739.md)|'*número*': las dimensiones de matriz administrada o WinRT explícita deben estar comprendido entre 1 y 32.|
|C2740 de Error del compilador|valor del operando '*número*'está fuera del intervalo'*lower_bound* - *upper_bound*'|
|C2741 de Error del compilador|tamaño de trama demasiado grande|
|C2742 de Error del compilador|Obsoleto.|
|[Error del compilador C2743](compiler-error-c2743.md)|'*tipo*': no se puede detectar un tipo nativo con el destructor __clrcall o el constructor de copias|
|C2744 de Error del compilador|'*operador*' no es un operador CLR o WinRT válido|
|[Error del compilador C2745](compiler-error-c2745.md)|'*token*': no se puede convertir este token a un identificador|
|C2746 de Error del compilador|Obsoleto.|
|C2747 de Error del compilador|Obsoleto.|
|[Error del compilador C2748](compiler-error-c2748.md)|creación de una matriz administrada o WinRT debe tener el tamaño de matriz o un inicializador de matriz|
|[Error del compilador C2749](compiler-error-c2749.md)|'*tipo*': solamente puede producir o detectar el identificador a una clase administrada con/CLR: safe|
|[Error del compilador C2750](compiler-error-c2750.md)|'*tipo*': no se puede usar 'new' en la referencia de tipo; Utilice 'gcnew' en su lugar|
|[Error del compilador C2751](compiler-error-c2751.md)|'*parámetro*': no se puede calificar el nombre de un parámetro de función|
|[Error del compilador C2752](compiler-error-c2752.md)|'*plantilla*': más de una especialización parcial coincide con la lista de argumentos de plantilla|
|[Error del compilador C2753](compiler-error-c2753.md)|'*plantilla*': la especialización parcial no puede coincidir con la lista de argumentos de plantilla principal|
|[Error del compilador C2754](compiler-error-c2754.md)|'*plantilla*': una especialización parcial no puede tener un parámetro de plantilla sin tipo dependiente|
|[Error del compilador C2755](compiler-error-c2755.md)|'*parámetro*': parámetro sin tipo de una especialización parcial debe ser un identificador simple|
|[Error del compilador C2756](compiler-error-c2756.md)|'*plantilla*': no se permite en una especialización parcial de argumentos de plantilla predeterminados|
|[Error del compilador C2757](compiler-error-c2757.md)|'*identificador*': ya existe un símbolo con este nombre y, por tanto, no se puede usar este nombre como un nombre de espacio de nombres|
|[Error del compilador C2758](compiler-error-c2758.md)|'*miembro*': se debe inicializar un miembro de tipo de referencia|
|C2759 de Error del compilador|informes de ensamblador en línea: *error_message*|
|[Error del compilador C2760](compiler-error-c2760.md)|error de sintaxis: se esperaba '*símbolo1*'not'*token2*'|
|[Error del compilador C2761](compiler-error-c2761.md)|'*función*': nueva declaración de función miembro no permitida|
|[Error del compilador C2762](compiler-error-c2762.md)|'*plantilla*': expresión no válida como argumento de plantilla para '*parámetro*'|
|C2763 de Error del compilador|'*plantilla*': uso no válido de un literal de cadena como argumento de plantilla para '*parámetro*'|
|[Error del compilador C2764](compiler-error-c2764.md)|'*parámetro*': parámetro de plantilla no utilizado o deducible en la especialización parcial '*especialización*'|
|[Error del compilador C2765](compiler-error-c2765.md)|'*función*': una especialización explícita de una plantilla de función no puede tener ningún argumento predeterminado|
|[Error del compilador C2766](compiler-error-c2766.md)|especialización explícita; '*especialización*' ya se ha definido|
|[Error del compilador C2767](compiler-error-c2767.md)|Error de coincidencia de dimensión de matriz administrada o WinRT: se esperaba *número* argumentos n - *número* proporcionada|
|[Error del compilador C2768](compiler-error-c2768.md)|'*función*': uso no válido de argumentos de plantilla explícitos|
|C2769 de Error del compilador|no puede inicializar llave de una matriz administrada o WinRT en una lista de inicializadores de base/miembro|
|[Error del compilador C2770](compiler-error-c2770.md)|argumentos de plantilla/genérica explícita no válido para '*plantilla*'|
|[Error del compilador C2771](compiler-error-c2771.md)|#import solo se permite en un ámbito global o de espacio de nombres|
|C2772 de Error del compilador|Obsoleto.|
|[Error del compilador C2773](compiler-error-c2773.md)|#import y #using disponible solo en el compilador de C++|
|[Error del compilador C2774](compiler-error-c2774.md)|'*identificador*': no hay ningún método 'put' está asociado a esta propiedad|
|[Error del compilador C2775](compiler-error-c2775.md)|'*identificador*': no hay ningún método 'get' está asociado a esta propiedad|
|[Error del compilador C2776](compiler-error-c2776.md)|se puede especificar un solo método 'get' por propiedad|
|[Error del compilador C2777](compiler-error-c2777.md)|se puede especificar un único método 'put' por propiedad|
|[Error del compilador C2778](compiler-error-c2778.md)|GUID formado incorrectamente en __declspec(uuid())|
|[Error del compilador C2779](compiler-error-c2779.md)|'*declaración*': los métodos de propiedad solo puede asociarse con miembros de datos no estáticos|
|[Error del compilador C2780](compiler-error-c2780.md)|'*declaración*': espera *número* argumentos - *número* proporcionada|
|[Error del compilador C2781](compiler-error-c2781.md)|'*declaración*': espera al menos *número* argumento - *número* proporcionada|
|[Error del compilador C2782](compiler-error-c2782.md)|'*declaración*': parámetro de plantilla/generic '*parámetro*' es ambiguo|
|[Error del compilador C2783](compiler-error-c2783.md)|'*declaración*': no se pudo deducir el argumento de plantilla o genérico para '*identificador*'|
|[Error del compilador C2784](compiler-error-c2784.md)|'*declaración*': no se pudo deducir el argumento de plantilla o genérico para '*type1*'from'*type2*'|
|[Error del compilador C2785](compiler-error-c2785.md)|'*declaration1*'y'*declaration2*' tienen distintos tipos de valor devueltos|
|[Error del compilador C2786](compiler-error-c2786.md)|'*tipo*': operando no válido para __uuidof|
|[Error del compilador C2787](compiler-error-c2787.md)|'*identificador*': ningún GUID se ha asociado a este objeto|
|[Error del compilador C2788](compiler-error-c2788.md)|'*identificador*': más de un GUID asociado a este objeto|
|C2789 de Error del compilador|'*identificador*': se debe inicializar un objeto de tipo calificado como const;|
|[Error del compilador C2790](compiler-error-c2790.md)|'super': esta palabra clave solo puede usarse dentro del cuerpo de función miembro de clase|
|[Error del compilador C2791](compiler-error-c2791.md)|uso no válido de 'super': '*clase*' no tiene clases base|
|[Error del compilador C2792](compiler-error-c2792.md)|'super': esta palabra clave debe ir seguida por '::'|
|[Error del compilador C2793](compiler-error-c2793.md)|'*token*': siguiente token inesperado '::', identificador o la palabra clave 'operator' se esperaba|
|[Error del compilador C2794](compiler-error-c2794.md)|'*identificador*': no es miembro de ninguna clase base directa o indirecta de '*clase*'|
|[Error del compilador C2795](compiler-error-c2795.md)|' super::*identificador*' no es una función miembro|
|C2796 de Error del compilador|'ref new' solo puede usarse para crear una instancia de un tipo WinRT|
|[Error del compilador C2797](compiler-error-c2797.md)|(Obsoleto) '*identificador*': no se ha implementado la inicialización de la lista dentro de la lista de inicializadores de miembro o un inicializador de miembro de datos no estáticos|
|[Error del compilador C2798](compiler-error-c2798.md)|' super::*identificador*' es ambiguo|
|C2799 de Error del compilador|'*identificador*': se debe inicializar un objeto de tipo calificado como const; clase sin un constructor predeterminado proporcionado por el usuario|
