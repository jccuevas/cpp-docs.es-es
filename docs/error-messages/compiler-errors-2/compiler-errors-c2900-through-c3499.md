---
title: "C2900 de errores del compilador a través de C2999 | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2900
- C2901
- C2905
- C2907
- C2915
- C2916
- C2922
- C2924
- C2925
- C2926
- C2938
- C2949
- C2950
- C2954
- C2956
- C2960
- C2961
- C2963
- C2964
- C2965
- C2966
- C2967
- C2968
- C2972
- C2980
- C2981
- C2982
- C2983
- C2984
- C2985
- C2986
- C2987
- C2997
- C2999
helpviewer_keywords:
- C2900
- C2901
- C2905
- C2907
- C2915
- C2916
- C2922
- C2924
- C2925
- C2926
- C2938
- C2949
- C2950
- C2954
- C2956
- C2960
- C2961
- C2963
- C2964
- C2965
- C2966
- C2967
- C2968
- C2972
- C2980
- C2981
- C2982
- C2983
- C2984
- C2985
- C2986
- C2987
- C2997
- C2999
dev_langs: C++
ms.assetid: e3440738-e11b-4878-9ae3-6bc6c53ba461
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 535a1d42d9d43022bbf513b72bac18dd5accad82
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-errors-c2900-through-c2999"></a>C2900 de errores del compilador a través de C2999
Los artículos de esta parte de la documentación contienen información sobre una subsección de los errores del compilador de Visual C++. Puede tener acceso a información aquí o bien, en la ventana de **salida** de Visual Studio, puede seleccionar un número de error y elegir después la tecla F1.  
  
> [!NOTE]
>  No todos [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] error está documentado en MSDN. En muchos casos, el mensaje de diagnóstico proporciona toda la información que está disponible. Si cree que un mensaje de error necesita una explicación adicional, puede enviarnos su opinión. Puede utilizar el formulario de comentarios de esta página, o vaya a la barra de menús de Visual Studio y elija **ayuda**, **notificar un error**, o puede enviar un informe de sugerencia o un error en [Microsoft Connect](http://connect.microsoft.com/VisualStudio).  
  
 Puede encontrar ayuda adicional sobre errores y advertencias en los foros públicos de MSDN. El [lenguaje Visual C++](http://go.microsoft.com/fwlink/?LinkId=158195) es foro para preguntas y debate sobre el [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] sintaxis del lenguaje y compilador. El [General de Visual C++](http://go.microsoft.com/fwlink/?LinkId=158194) es foro para preguntas sobre [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] que no se debaten en otros foros. También puede encontrar ayuda sobre los errores y advertencias en [desbordamiento de la pila](http://stackoverflow.com/).  
  
|Error|Mensaje|  
|-----------|-------------|  
|C2900 de Error del compilador|'*declarador*': plantillas de función miembro en clases de WinRT deben ser 'private', 'interno' o 'protected private'|  
|C2901 de Error del compilador|'*identificador*': una interfaz genérica o delegado no puede ser público|  
|[Error del compilador C2902](compiler-error-c2902.md)|'*token*': inesperado token siguiente 'template/generic', se esperaba un identificador|  
|[Error del compilador C2903](compiler-error-c2903.md)|'*identificador*': símbolo no es una plantilla de clase/generic ni una plantilla de función/generic|  
|[Error del compilador C2904](compiler-error-c2904.md)|'*identificador*': nombre que ya se utiliza para una plantilla en el ámbito actual|  
|C2905 de Error del compilador|Obsoleto.|  
|[Error del compilador C2906](compiler-error-c2906.md)|'*plantilla*': una especialización explícita requiere 'plantilla <>'|  
|C2907 de Error del compilador|el argumento de registro '*número*' no especifica el número de registro válido|  
|[Error del compilador C2908](compiler-error-c2908.md)|especialización explícita; '*plantilla*' ya se han creado instancias|  
|[Error del compilador C2909](compiler-error-c2909.md)|'*identificador*': creación de instancias explícita de la plantilla de función requiere el tipo de valor devuelto|  
|[Error del compilador C2910](compiler-error-c2910.md)|'*función*': no se puede especializar de forma explícita|  
|[Error del compilador C2911](compiler-error-c2911.md)|'*miembro*': no se puede declarar ni definir en el ámbito actual|  
|[Error del compilador C2912](compiler-error-c2912.md)|especialización explícita '*declaración*' no es una especialización de una plantilla de función|  
|[Error del compilador C2913](compiler-error-c2913.md)|especialización explícita; '*declaración*' no es una especialización de una plantilla de clase|  
|[Error del compilador C2914](compiler-error-c2914.md)|'*identificador*': no se puede deducir el argumento de plantilla o genérico como argumento de función es ambiguo|  
|C2915 de Error del compilador|'*identificador*': '*tipo*' no se puede usar directamente en la superficie publicada de un tipo WinRT. Use ' Platform:: Object ^' en su lugar para pasar este tipo|  
|C2916 de Error del compilador|'*identificador*': [FlagsAttribute] (sólo) debe especificarse en una enumeración pública con 'unsigned int' tipo subyacente|  
|[Error del compilador C2917](compiler-error-c2917.md)|'*identificador*': parámetro de plantilla no válido|  
|[Error del compilador C2918](compiler-error-c2918.md)|'*identificador*': no se puede usar propiedades indizadas en la superficie publicada de un tipo WinRT|  
|[Error del compilador C2919](compiler-error-c2919.md)|'*tipo*': no se puede usar operadores en la superficie publicada de un tipo WinRT|  
|[Error del compilador C2920](compiler-error-c2920.md)|nueva definición: '*tipo*': clase de plantilla o genérico ya se ha declarado como*declaración*'|  
|[Error del compilador C2921](compiler-error-c2921.md)|nueva definición: '*tipo*': clase de plantilla o genérico se está declarando de nuevo como*declaración*'|  
|C2922 de Error del compilador|'*interfaz*': WinRT de una interfaz no puede contener miembros estáticos|  
|[Error del compilador C2923](compiler-error-c2923.md)|'*tipo*': '*identificador*'no es un argumento de tipo template/generic válido para el parámetro'*parámetro*'|  
|C2924 de Error del compilador|argumento de la rutina __declspec (interrupción) no está en R2|  
|C2925 de Error del compilador|rutina __declspec (interrupción) no se puede utilizar punto flotante|  
|C2926 de Error del compilador|'*identificador*': no se permite un inicializador de miembro predeterminado para un miembro de un struct anónimo dentro de una unión|  
|[Error del compilador C2927](compiler-error-c2927.md)|'*identificador*': una plantilla de función debe llamarse con al menos un argumento|  
|[Error del compilador C2928](compiler-error-c2928.md)|creación de instancias explícita; '*identificador*'no es una función o un miembro de datos estáticos de clase de plantilla'*clase*'|  
|[Error del compilador C2929](compiler-error-c2929.md)|'*declarador*': creación de instancias explícita; explícitamente no se puede forzar y suprimir la creación de instancias de miembro de clase de plantilla|  
|[Error del compilador C2930](compiler-error-c2930.md)|'*clase*': Id. de plantilla-identificador genérico volvió a definir como enumerador de ' enum *identificador*'|  
|[Error del compilador C2931](compiler-error-c2931.md)|'*class1*': Id. de plantilla: identificador genérico volvió a definir como una función miembro de '*clase2*'|  
|[Error del compilador C2932](compiler-error-c2932.md)|'*tipo*': Id. de plantilla: identificador genérico volvió a definir como un miembro de datos de '*identificador*'|  
|[Error del compilador C2933](compiler-error-c2933.md)|'*tipo*': Id. de plantilla: identificador genérico volvió a definir como miembro typedef de '*identificador*'|  
|[Error del compilador C2934](compiler-error-c2934.md)|'*tipo*': Id. de plantilla-identificador genérico volvió a definir como un anidada '*elemento*'of'*identificador*'|  
|[Error del compilador C2935](compiler-error-c2935.md)|'*tipo*': Id. de plantilla: identificador genérico volvió a definir como función global|  
|[Error del compilador C2936](compiler-error-c2936.md)|'*tipo*': Id. de plantilla-identificador genérico volvió a definir como variable de datos global|  
|[Error del compilador C2937](compiler-error-c2937.md)|'*tipo*': Id. de plantilla: identificador genérico volvió a definir como typedef global|  
|C2938 de Error del compilador|'*identificador*': no se pudo especializar la plantilla de alias|  
|[Error del compilador C2939](compiler-error-c2939.md)|'*tipo*': Id. de plantilla: identificador genérico volvió a definir como variable de datos local|  
|[Error del compilador C2940](compiler-error-c2940.md)|'*tipo*': Id. de plantilla: identificador genérico volvió a definir como typedef local|  
|[Error del compilador C2941](compiler-error-c2941.md)|'*tipo*': Id. de plantilla: identificador genérico volvió a definir como una variable local '*elemento*'|  
|[Error del compilador C2942](compiler-error-c2942.md)|'*tipo*': Id. de plantilla: identificador genérico volvió a definir como argumento formal de una función|  
|[Error del compilador C2943](compiler-error-c2943.md)|'*tipo*': Id. de plantilla-identificador genérico volvió a definir como argumento de tipo de una plantilla|  
|[Error del compilador C2944](compiler-error-c2944.md)|'*tipo*': Id. de plantilla: identificador genérico volvió a definir como argumento de valor de una plantilla|  
|[Error del compilador C2945](compiler-error-c2945.md)|la creación de instancias explícita no hace referencia a una especialización de clase de plantilla|  
|[Error del compilador C2946](compiler-error-c2946.md)|creación de instancias explícita; '*tipo*' no es una especialización de clase de plantilla|  
|[Error del compilador C2947](compiler-error-c2947.md)|se esperaba ' >' para terminar los argumentos de plantilla, se encontró '*token*'|  
|[Error del compilador C2948](compiler-error-c2948.md)|creación de instancias explícita; especificador de clase de almacenamiento '*especificador*' no está permitido en la especialización|  
|C2949 de Error del compilador|thread_local no se admite con/kernel|  
|Error del compilador C2950|Obsoleto.|  
|[Error del compilador C2951](compiler-error-c2951.md)|las declaraciones de plantilla o genérico solo se permiten en el espacio de nombres global, o ámbito de clase|  
|[Error del compilador C2952](compiler-error-c2952.md)|'*declaración*': falta la lista de parámetros de plantilla o genérico de la declaración de plantilla/generic|  
|[Error del compilador C2953](compiler-error-c2953.md)|'*tipo*': ya se ha definido la plantilla de clase|  
|C2954 de Error del compilador|argumento de palabra de instrucción fuera del intervalo|  
|[Error del compilador C2955](compiler-error-c2955.md)|'*tipo*': el uso de plantilla de clase/generic requiere la lista de argumentos de plantilla/generic|  
|C2956 de Error del compilador|desasignación dimensionada función 'operator delete (void *, size_t)' se elegiría como función de desasignación de selección de ubicación.|  
|[Error del compilador C2957](compiler-error-c2957.md)|'*token*': delimitador izquierdo no válido: se esperaba ' <'|  
|[Error del compilador C2958](compiler-error-c2958.md)|la izquierda *delimitador* encontrado en '*archivo*(*line_number*)' no coincidió con correctamente|  
|[Error del compilador C2959](compiler-error-c2959.md)|una función o clase genérica no puede ser un miembro de una plantilla|  
|C2960 de Error del compilador|Obsoleto.|  
|C2961 de Error del compilador|'*función*': instancias explícitas incoherentes, una instancia explícita anterior no especificó '*argumento*'|  
|[Error del compilador C2962](compiler-error-c2962.md)|error de sintaxis: '*token*': se esperaba la definición de función miembro de clase de plantilla finalizase con '}'|  
|Error del compilador C2963|Obsoleto.|  
|Error del compilador C2964|Obsoleto.|  
|C2965 de Error del compilador|__declspec (*especificador*) no es compatible con/kernel|  
|C2966 de Error del compilador|'*identificador1*': debe tener el mismo __declspec(code_seg(...)) como su clase base*identificador2*'|  
|C2967 de Error del compilador|'*identificador*': una función virtual de reemplaza debe tener el mismo __declspec(code_seg(...)) como una función virtual invalidada|  
|C2968 de Error del compilador|'*identificador*': declaración de alias recursiva|  
|[Error del compilador C2969](compiler-error-c2969.md)|error de sintaxis: '*token*': se esperaba la definición de función miembro finalizase con '}'|  
|[Error del compilador C2970](compiler-error-c2970.md)|'*tipo*': parámetro de plantilla '*parámetro*': '*argumento*': no se puede usar una expresión que contenga objetos con vinculación interna como un argumento sin tipo|  
|[Error del compilador C2971](compiler-error-c2971.md)|'*tipo*': parámetro de plantilla '*parámetro*': '*argumento*': no se puede usar una variable con una duración de almacenamiento no estático como un argumento sin tipo|  
|C2972 de Error del compilador|'*tipo*': parámetro de plantilla '*parámetro*': el tipo de argumento de tipo no es válido|  
|[Error del compilador C2973](compiler-error-c2973.md)|'*plantilla*': argumento de plantilla no válido '*número*'|  
|[Error del compilador C2974](compiler-error-c2974.md)|'*tipo*': argumento de plantilla/generic no válido para '*parámetro*', tipo esperado|  
|[Error del compilador C2975](compiler-error-c2975.md)|'*tipo*': argumento de plantilla no válido para '*parámetro*', se esperaba una expresión constante de tiempo de compilación|  
|[Error del compilador C2976](compiler-error-c2976.md)|'*tipo*': hay suficientes argumentos de plantilla/generic|  
|[Error del compilador C2977](compiler-error-c2977.md)|'*tipo*': hay demasiados argumentos de plantilla/generic|  
|[Error del compilador C2978](compiler-error-c2978.md)|error de sintaxis: se esperaba '*palabraclave1*'o'*palabraclave2*'; se encontró el tipo'*tipo*'; no es de tipo no se admiten parámetros en genéricos|  
|[Error del compilador C2979](compiler-error-c2979.md)|no se admite especializaciones explícitas en genéricos|  
|C2980 de Error del compilador|Control de excepciones de C++ no es compatible con/kernel|  
|C2981 de Error del compilador|la forma dinámica de '*palabra clave*' no es compatible con/kernel|  
|C2982 de Error del compilador|'*declaración*': diferentes __declspec(code_seg(...)) usa: fue '*identificador1*"ahora"*identificador2*'|  
|C2983 de Error del compilador|'*declaración*': todas las declaraciones deben tener un __declspec(code_seg(...)) idénticos|  
|C2984 de Error del compilador|Obsoleto.|  
|C2985 de Error del compilador|'*argumento*': el argumento __declspec(code_seg(...)) debe ser una sección de texto|  
|C2986 de Error del compilador|'*identificador*': __declspec(code_seg(...)) solo puede aplicarse a una clase o una función|  
|C2987 de Error del compilador|una declaración no puede tener ambos __declspec (code_seg ('*identificador*')) y __declspec (code_seg ('*valor*'))|  
|[Error del compilador C2988](compiler-error-c2988.md)|declaración o definición de plantilla irreconocible|  
|[Error del compilador C2989](compiler-error-c2989.md)|'*clase*': clase de plantilla o genérico ya se ha declarado como una plantilla de clase no/generic|  
|[Error del compilador C2990](compiler-error-c2990.md)|'*clase*': clase sin plantilla/generic ya se ha declarado como una plantilla de clase/generic|  
|[Error del compilador C2991](compiler-error-c2991.md)|nueva definición del parámetro de plantilla/generic '*parámetro*'|  
|[Error del compilador C2992](compiler-error-c2992.md)|'*clase*': lista de parámetros de plantilla o genérico ausente o no válido|  
|[Error del compilador C2993](compiler-error-c2993.md)|'*tipo*': tipo no válido para el parámetro de plantilla sin tipo '*identificador*'|  
|[Error del compilador C2994](compiler-error-c2994.md)|clase sin nombre en la lista de parámetros de plantilla|  
|[Error del compilador C2995](compiler-error-c2995.md)|'*declaración*': ya se ha definido la plantilla de función|  
|[Error del compilador C2996](compiler-error-c2996.md)|'*función*': definición de plantilla de función recursiva|  
|C2997 de Error del compilador|'*función*': no se puede deducir el límite de la matriz de un inicializador de miembro predeterminado|  
|[Error del compilador C2998](compiler-error-c2998.md)|'*declarador*': no puede ser una definición de plantilla|  
|Error del compilador C2999|ERROR DESCONOCIDO Elija el comando soporte técnico en el menú Ayuda de Visual C++, o abra el archivo de Ayuda de soporte técnico para obtener más información|  
