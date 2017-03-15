---
title: "Using CString | Microsoft Docs"
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
  - "CString class (Visual C++)"
  - "CString objects, C++ string manipulation"
  - "CString objects, reference counting"
ms.assetid: ed018aaf-8b10-46f9-828c-f9c092dc7609
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Using CString
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En los temas de esta sección se describe cómo programar con `CString`.  Consulte la documentación relativa a la clase `CString` como referencia sobre esta[](../atl-mfc-shared/reference/cstringt-class.md "CStringT Class")clase.  
  
 Para usar `CString`, incluya el encabezado `atlstr.h`.  
  
 Las clases `CString`, `CStringA` y `CStringW` son especializaciones de una plantilla de clase denominada [CStringT](../atl-mfc-shared/reference/cstringt-class.md), que se basa en el tipo de datos de caracteres que admiten.  
  
 Un objeto `CStringW` contiene el tipo `wchar_t` y admite cadenas Unicode.  Un objeto `CStringA` contiene el tipo `char` y admite cadenas de un solo byte o multibyte \(MBCS\).  Un objeto `CString` admite el tipo `char` o el tipo `wchar_t`, dependiendo de si se ha definido el símbolo `MBCS` o el símbolo `UNICODE` en el tiempo de compilación.  
  
 Un objeto `CString` conserva los datos de caracteres en un objeto `CStringData`.  `CString` acepta cadenas de estilo C terminadas en `null`, pero no conserva el carácter `null` en los datos de caracteres almacenados.  En su lugar, `CString` realiza un seguimiento de la longitud de la cadena.  `CString` sí proporciona un terminador nulo cuando exporta una cadena de estilo C.  Se puede insertar un elemento `null` en `CString`, pero esto podría generar resultados inesperados.  
  
 El siguiente conjunto de clases de cadena se puede usar sin vincular a una biblioteca MFC, tanto si hay o no compatibilidad de CRT: `CAtlString`, `CAtlStringA` y `CAtlStringW`.  
  
 `CString` se usa en objetos nativos.  En los proyectos de código administrado \(C\+\+\/CLI\), use `System::String`.  
  
 Para agregar más capacidades de las que `CString`, `CStringA` o `CStringW` ofrecen actualmente, conviene crear una subclase de `CStringT` que contenga las características extra.  
  
 El siguiente código muestra cómo crear una `CString` e imprimirla en una salida estándar:  
  
```cpp  
#include <atlstr.h>  
  
int main() {  
    CString aCString = CString(_T("A string"));  
    _tprintf(_T("%s"), (LPCTSTR) aCString);  
}  
```  
  
## En esta sección  
 [Operaciones básicas de CString](../atl-mfc-shared/basic-cstring-operations.md)  
 Se describen las operaciones básicas de `CString`, por ejemplo, cómo crear objetos a partir de cadenas literales de C, cómo acceder a caracteres individuales de una `CString`, cómo concatenar dos objetos y cómo comparar objetos `CString`.  
  
 [Administración de datos de cadena](../atl-mfc-shared/string-data-management.md)  
 Se aborda el uso de Unicode y MBCS con `CString`.  
  
 [Semántica de CString](../atl-mfc-shared/cstring-semantics.md)  
 Se explica el uso de objetos `CString`.  
  
 [Operaciones de CString relacionadas con cadenas de estilo C](../atl-mfc-shared/cstring-operations-relating-to-c-style-strings.md)  
 Se describe cómo manipular el contenido de un objeto `CString` como una cadena terminada en un valor nulo de estilo C.  
  
 [Asignación y liberación de memoria para un BSTR](../atl-mfc-shared/allocating-and-releasing-memory-for-a-bstr.md)  
 Se explica el uso de memoria en relación con un `BSTR` y objetos COM.  
  
 [Limpieza de excepciones de CString](../atl-mfc-shared/cstring-exception-cleanup.md)  
 Se explica que la limpieza expresa en MFC 3.0 y en versiones posteriores ya no es necesaria.  
  
 [Paso de argumentos de CString](../atl-mfc-shared/cstring-argument-passing.md)  
 Se detalla cómo pasar objetos CString a funciones y cómo obtener objetos `CString` de las funciones.  
  
 [Compatibilidad con Unicode y con el juego de caracteres multibyte \(MBCS\)](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)  
 Se centra en cómo MFC permite el uso de Unicode y MBCS.  
  
## Referencia  
 [CStringT](../atl-mfc-shared/reference/cstringt-class.md)  
 Contiene información de referencia sobre la clase `CStringT`.  
  
 [CSimpleStringT Class](../atl-mfc-shared/reference/csimplestringt-class.md)  
 Contiene información de referencia sobre la clase `CSimpleStringT`.  
  
## Secciones relacionadas  
 [Cadenas](../atl-mfc-shared/strings-atl-mfc.md)  
 Contiene vínculos a temas en los que se describen las diversas formas de administrar datos de cadena.  
  
 [Crear instancias de plantillas de clase](../Topic/Class%20Template%20Instantiation.md)  
 `CString` es un `typedef` basado en `CStringT`, que es instancia de una especialización de una plantilla de clase.