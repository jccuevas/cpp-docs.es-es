---
title: "CString Operations Relating to C-Style Strings | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "casting CString objects"
  - "CString objects, operaciones básicas"
  - "C-style strings"
  - "MFC [C++], string handling class"
  - "valores nulos, Null-terminated string conversion"
  - "standard run-time library string functions"
  - "string arguments"
  - "conversión de cadenas [C++], C-style strings"
  - "funciones de cadena"
  - "cadenas [C++], class CString"
  - "cadenas [C++], in C"
  - "cadenas [C++], string operations"
ms.assetid: 5048de8a-5298-4891-b8a0-c554b5a3ac1b
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# CString Operations Relating to C-Style Strings
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Un objeto [CString](../atl-mfc-shared/using-cstring.md) contiene datos de cadena de caracteres.  `CString` hereda el conjunto de [métodos y operadores](../atl-mfc-shared/reference/cstringt-class.md) definidos en la plantilla de clase [CStringT](../atl-mfc-shared/reference/cstringt-class.md) para trabajar con los datos de cadena  \(`CString` es un `typedef` que especializa `CStringT` para que trabaje con el tipo de datos de caracteres que `CString` admite\).  
  
 `CString` no almacena datos de caracteres internamente como una cadena terminada en un valor nulo de estilo C.  En su lugar, `CString` realiza un seguimiento de la longitud de los datos de caracteres para, así, poder vigilar los datos y el espacio que precisan de forma más segura.  
  
 Con todo, `CString` acepta cadenas de estilo C y ofrece formas de acceder a los datos de caracteres como una cadena de estilo C.  Este tema está compuesto por las siguientes secciones, donde se explica cómo usar un objeto `CString` como si fuera una cadena terminada en un valor nulo de estilo C.  
  
-   [Conversión a cadenas terminadas en un valor nulo de estilo C](#_core_using_cstring_as_a_c.2d.style_null.2d.terminated_string)  
  
-   [Uso de funciones de cadena de biblioteca en tiempo de ejecución estándar](#_core_working_with_standard_run.2d.time_library_string_functions)  
  
-   [Modificación directa del contenido de CString](#_core_modifying_cstring_contents_directly)  
  
-   [Uso de objetos CString con funciones de argumento variable](#_core_using_cstring_objects_with_variable_argument_functions)  
  
-   [Especificación de parámetros formales de CString](#_core_specifying_cstring_formal_parameters)  
  
##  <a name="_core_using_cstring_as_a_c.2d.style_null.2d.terminated_string"></a> Uso de CString como una cadena terminada en un valor nulo de estilo C  
 Para usar un objeto `CString` como una cadena de estilo C, convierta el objeto a `LPCTSTR`.  En el siguiente ejemplo, `CString` devuelve un puntero a una cadena terminada en un valor nulo de estilo C de solo lectura.  La función `strcpy` coloca una copia de esa cadena de estilo C en la variable `myString`.  
  
```  
CString aCString = "A string";  
char myString[256];  
strcpy(myString, (LPCTSTR)aCString);  
  
```  
  
 Puede usar métodos de `CString` \(`SetAt`, por ejemplo\) para modificar caracteres concretos del objeto de cadena.  Sin embargo, el puntero `LPCTSTR` es temporal y deja de ser válido en cuanto se efectúa un cambio en `CString`.  `CString` también puede quedar fuera de su ámbito y eliminarse automáticamente.  Le recomendamos obtener un puntero `LPCTSTR` actualizado de un objeto `CString` cada vez que vaya a usar uno.  
  
 Habrá veces en las que necesite una copia de los datos de `CString` para modificarlos directamente.  Use la función más protegida `strcpy_s` \(o la función portable de Unicode\/MBCS `_tcscpy_s`\) para copiar el objeto `CString` en otro búfer.  Ahí, los caracteres se podrán modificar con menor riesgo, como verá en este ejemplo.  
  
 [!code-cpp[NVC_ATLMFC_Utilities#189](../atl-mfc-shared/codesnippet/CPP/cstring-operations-relating-to-c-style-strings_1.cpp)]  
  
> [!NOTE]
>  El tercer argumento para `strcpy_s` \(o la función portable de Unicode\/MBCS `_tcscpy_s`\) es un `const``wchar_t*` \(Unicode\) o un `const``char*` \(ANSI\).  En el ejemplo anterior se pasa un `CString` para este argumento.  El compilador de C\+\+ emplea automáticamente la función de conversión definida para la clase `CString`, que convierte un `CString` en un `LPCTSTR`.  La posibilidad de definir operaciones de conversión de un tipo a otro es una de las características más útiles de C\+\+.  
  
##  <a name="_core_working_with_standard_run.2d.time_library_string_functions"></a> Uso de funciones de cadena de biblioteca en tiempo de ejecución estándar  
 Debe poder encontrar un método de `CString` para realizar cualquier operación de cadena en la que puedan usarse funciones de cadena de biblioteca en tiempo de ejecución estándar, como `strcmp` \(o la función portable de Unicode\/MBCS `_tcscmp`\).  
  
 En caso de que deba usar funciones de cadena de biblioteca en tiempo de ejecución de C, puede recurrir a las técnicas descritas en \_core\_using\_cstring\_as\_a\_c.2d.style\_null.2d.terminated\_string.  Puede copiar el objeto `CString` en un búfer de cadena de estilo C equivalente, llevar a cabo las operaciones que correspondan en dicho búfer y, luego, asignar la cadena de estilo C resultante de vuelta a un objeto `CString`.  
  
##  <a name="_core_modifying_cstring_contents_directly"></a> Modificación directa del contenido de CString  
 La mayoría de las veces, conviene usar las funciones miembro de `CString` para modificar el contenido de un objeto `CString` o para convertir `CString` en una cadena de caracteres de estilo C.  
  
 Existen algunas situaciones en las que sí tiene sentido modificar el contenido de `CString` directamente \(por ejemplo, al trabajar con funciones de sistema operativo que requieren un búfer de caracteres\).  
  
 Los métodos `GetBuffer` y `ReleaseBuffer` dan acceso al búfer de caracteres interno de un objeto `CString`, donde podrá modificarlo directamente.  En los siguientes pasos se explica cómo usar estas funciones con este fin.  
  
#### Para usar GetBuffer y ReleaseBuffer para acceder al búfer de caracteres interno de un objeto CString  
  
1.  Llame a `GetBuffer` en relación con un objeto `CString` e indique la longitud de búfer que necesita.  
  
2.  Use el puntero que `GetBuffer` devuelve para escribir caracteres directamente en el objeto `CString`.  
  
3.  Llame a `ReleaseBuffer` en relación con el objeto `CString` para actualizar toda la información de estado de `CString` interna \(por ejemplo, la longitud de la cadena\).  Tras modificar el contenido de un objeto `CString` directamente, debe llamar a `ReleaseBuffer` antes de llamar a cualquier otra función miembro de `CString`.  
  
##  <a name="_core_using_cstring_objects_with_variable_argument_functions"></a> Uso de objetos CString con funciones de argumento variable  
 Algunas funciones de C toman un número variable de argumentos.  Un ejemplo significativo de esto es `printf_s`.  Debido al modo en que esta función se declara, el compilador no puede saber con seguridad de qué tipo son los argumentos ni distinguir qué operación de conversión debe realizar en cada argumento.  Por lo tanto, es fundamental usar una conversión de tipo explícita al pasar un objeto `CString` a una función que toma un número variable de argumentos.  
  
 Para usar un objeto `CString` en una función de argumento variable, convierta explícitamente el objeto `CString` en una cadena `LPCTSTR`, como se indica en el siguiente ejemplo.  
  
 [!code-cpp[NVC_ATLMFC_Utilities#190](../atl-mfc-shared/codesnippet/CPP/cstring-operations-relating-to-c-style-strings_2.cpp)]  
  
##  <a name="_core_specifying_cstring_formal_parameters"></a> Especificación de parámetros formales de CString  
 En la mayoría de las funciones que necesitan un argumento de cadena, lo mejor es especificar el parámetro formal en el prototipo de la función como un puntero `const` a un carácter \(`LPCTSTR`\), y no un `CString`.  Cuando un parámetro formal se especifica como un puntero `const` a un carácter, se puede pasar un puntero a una matriz de `TCHAR`, una cadena literal \[`"hi there"`\] o un objeto `CString`.  El objeto `CString` se convertirá automáticamente en un `LPCTSTR`.  Podrá usar un objeto `CString` en cualquier parte donde pueda usar un `LPCTSTR`.  
  
 Si el argumento no se va a modificar, también puede especificar un parámetro formal como una referencia de cadena de constante \(es decir, `const``CString&`\).  Quite el modificador `const` si la cadena se va a modificar mediante la función.  Si se pretende obtener un valor nulo predeterminado, inicialícelo en la cadena null \[`""`\], como se muestra aquí:  
  
 [!code-cpp[NVC_ATLMFC_Utilities#191](../atl-mfc-shared/codesnippet/CPP/cstring-operations-relating-to-c-style-strings_3.cpp)]  
  
 Para la mayoría de los resultados de función, se puede devolver simplemente un objeto `CString` por valor.  
  
## Vea también  
 [Cadenas](../atl-mfc-shared/strings-atl-mfc.md)   
 [CString Argument Passing](../atl-mfc-shared/cstring-argument-passing.md)