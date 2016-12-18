---
title: "Basic CString Operations | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "caracteres, accessing in CStrings"
  - "CString objects"
  - "CString objects, operaciones básicas"
  - "literal strings, CString operations"
  - "comparación de cadenas, CString operations"
  - "literales de cadena, CString operations"
ms.assetid: 41db66b2-9427-4bb3-845a-9b6869159a6c
caps.latest.revision: 17
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Basic CString Operations
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Este tema describe las operaciones básicas siguientes de [CString](../atl-mfc-shared/reference/cstringt-class.md) :  
  
-   [Crear objetos CString de cadenas literales estándar de C](#_core_creating_cstring_objects_from_standard_c_literal_strings)  
  
-   [Caracteres individuales de un objeto CString](#_core_accessing_individual_characters_in_a_cstring)  
  
-   [Concatenar dos objetos CString](#_core_concatenating_two_cstring_objects)  
  
-   [Comparar objetos CString](#_core_comparing_cstring_objects)  
  
-   [Convertir los objetos CString](#_core_converting_cstring_objects)  
  
 `Class CString` se basa en la plantilla [CStringT Class](../atl-mfc-shared/reference/cstringt-class.md)de la clase.  `CString` es `typedef` de `CStringT`.  Más concretamente, `CString` es `typedef`*de una especialización explícita* de `CStringT`, que es una manera común de utilizar una plantilla de clase para definir una clase.  Las clases de igual forma definido son `CStringA` y `CStringW`.  Para obtener más información sobre la especialización explícita, vea [Crear instancias de plantillas de clase](../Topic/Class%20Template%20Instantiation.md).  
  
 `CString`, `CStringA`, y `CStringW` se definen en atlstr.h.  `CStringT` se define en cstringt.h.  
  
 `CString`, `CStringA`, y `CStringW` cada obtienen un conjunto de los métodos y operadores definidos por `CStringT` con datos de cadena que admiten.  Parte del duplicado de métodos y, supera en algunos casos los servicios de la cadena de las bibliotecas en tiempo de ejecución de C.  
  
 Nota: `CString` es una clase nativa.  Para una clase de la cadena que está para el uso en proyecto administrado de C\/C\+\+., puede utilizar `System.String`.  
  
##  <a name="_core_creating_cstring_objects_from_standard_c_literal_strings"></a> Crear objetos CString de cadenas literales estándar de C  
 Puede asignar cadenas literales de C a `CString` igual que puede asignar un objeto de `CString` a otro.  
  
-   Asigne el valor de la cadena literal de C\/C\+\+. a un objeto de `CString` .  
  
     [!code-cpp[NVC_ATLMFC_Utilities#183](../atl-mfc-shared/codesnippet/CPP/basic-cstring-operations_1.cpp)]  
  
-   Asigne el valor de un `CString` a otro objeto de `CString` .  
  
     [!code-cpp[NVC_ATLMFC_Utilities#184](../atl-mfc-shared/codesnippet/CPP/basic-cstring-operations_2.cpp)]  
  
     El contenido de un objeto de `CString` se copian cuando un objeto de `CString` está asignado a otro.  Por lo tanto, las dos cadenas no comparten una referencia a caracteres reales que constituyen la cadena.  Para obtener más información sobre cómo utilizar los objetos de `CString` como valores, vea [CString Semantics](../atl-mfc-shared/cstring-semantics.md).  
  
    > [!NOTE]
    >  Para escribir la aplicación para que se pueda compilar para Unicode o para ANSI, cadenas literales de código mediante la macro de \_T.  Para obtener más información, vea [Compatibilidad con Unicode y con el juego de caracteres multibyte \(MBCS\)](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md).  
  
##  <a name="_core_accessing_individual_characters_in_a_cstring"></a> Caracteres individuales de un objeto CString  
 Puede tener acceso a los caracteres individuales de un objeto de `CString` mediante los métodos de `GetAt` y de `SetAt` .  También puede utilizar el elemento de matriz, o subíndice, operador \( \[ \] \) en lugar de `GetAt` para obtener los caracteres individuales.  \(Esto es similar a los elementos de una matriz de acceso al lado del índice, como en cadenas estándar de C.\) Los valores de índice por caracteres de `CString` cero\-se basan.  
  
##  <a name="_core_concatenating_two_cstring_objects"></a> Concatenar dos objetos CString  
 Para concatenar dos objetos de `CString` , utilice los operadores de concatenación \(\+ o \+\=\), como sigue.  
  
 [!code-cpp[NVC_ATLMFC_Utilities#185](../atl-mfc-shared/codesnippet/CPP/basic-cstring-operations_3.cpp)]  
  
 Al menos un argumento operadores de concatenación \(\+ o \+\=\) debe ser un objeto de `CString` , pero puede utilizar una cadena de caracteres constante \(por ejemplo, `"big"`\) o `char` \(por ejemplo, “x "\) para el otro argumento.  
  
##  <a name="_core_comparing_cstring_objects"></a> Comparar objetos CString  
 El método de `Compare` y el operador \=\= para `CString` son equivalentes.  `Compare`, `operator==`, y `CompareNoCase` son MBCS y Unicode corriente; `CompareNoCase` también es sin distinción entre mayúsculas y minúsculas.  El método de `Collate` de `CString` es configuración regional\- sensible y suele ser más lento que `Compare`.  Utilice `Collate` sólo cuando debe seguir las reglas de ordenación según lo especificado por la configuración regional actual.  
  
 La tabla siguiente muestra las funciones disponibles y su equivalente Unicode\/MBCS\-portable de comparación de [CString](../atl-mfc-shared/reference/cstringt-class.md) funciones de la biblioteca en tiempo de ejecución de C.  
  
|Función CString|Función MBCS|Función Unicode|  
|---------------------|------------------|---------------------|  
|`Compare`|`_mbscmp`|`wcscmp`|  
|`CompareNoCase`|`_mbsicmp`|`_wcsicmp`|  
|`Collate`|`_mbscoll`|`wcscoll`|  
  
 En la plantilla de clase de `CStringT` define los operadores relacionales \(\<, \<\=, \>\=, \>, \=\=, y\! \=\), que están disponibles para uso de `CString`.  Puede comparar dos `CStrings` mediante estos operadores, como se muestra en el ejemplo siguiente.  
  
 [!code-cpp[NVC_ATLMFC_Utilities#186](../atl-mfc-shared/codesnippet/CPP/basic-cstring-operations_4.cpp)]  
  
##  <a name="_core_converting_cstring_objects"></a> Convertir los objetos CString  
 Para obtener información sobre cómo convertir objetos CString a otros tipos de cadena, vea [Cómo: Convertir entre distintos tipos de cadenas](../Topic/How%20to:%20Convert%20Between%20Various%20String%20Types.md).  
  
## Mediante CString con el wcout  
 Para utilizar un objeto CString con `wcout` debe convertir explícitamente el objeto a `const wchar_t*` tal y como se muestra en el ejemplo siguiente:  
  
```  
CString cs("meow");  
  wcout << (const wchar_t*) cs << endl;  
  
```  
  
 Sin la conversión, se trata `cs` mientras `void*` y `wcout` imprime la dirección del objeto.  Este comportamiento es provocado por las interacciones sutiles entre la deducción de argumento de plantilla y la resolución de sobrecarga que están en ellos mismos correctos y compatibles con el estándar de C\+\+.  
  
## Vea también  
 [Cadenas](../atl-mfc-shared/strings-atl-mfc.md)   
 [CStringT Class](../atl-mfc-shared/reference/cstringt-class.md)   
 [Crear instancias de plantillas de clase](../Topic/Class%20Template%20Instantiation.md)   
 [Especialización explícita de las plantillas de clase](../Topic/Explicit%20Specialization%20of%20Class%20Templates.md)   
 [Especialización parcial de plantillas de clase](../cpp/template-specialization-cpp.md)   
 [Cómo: Convertir entre distintos tipos de cadenas](../Topic/How%20to:%20Convert%20Between%20Various%20String%20Types.md)