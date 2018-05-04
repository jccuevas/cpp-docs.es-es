---
title: Uso de CString | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CString objects, C++ string manipulation
- CString objects, reference counting
- CString class (Visual C++)
ms.assetid: ed018aaf-8b10-46f9-828c-f9c092dc7609
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 591a319671ea42236af5ae7e80ea1cb94c3c446c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="using-cstring"></a>Uso de CString
En los temas de esta sección se describe cómo programar con `CString`. Para obtener documentación de referencia sobre la `CString` de clases, consulte la documentación de [CStringT](../atl-mfc-shared/reference/cstringt-class.md).  
  
 Para usar `CString`, incluya el encabezado `atlstr.h`.  
  
 El `CString`, `CStringA`, y `CStringW` clases son especializaciones de una plantilla de clase denominado [CStringT](../atl-mfc-shared/reference/cstringt-class.md) según el tipo de datos de caracteres que admiten.  
  
 Un objeto `CStringW` contiene el tipo `wchar_t` y admite cadenas Unicode. Un objeto `CStringA` contiene el tipo `char` y admite cadenas de un solo byte o multibyte (MBCS). Un objeto `CString` admite el tipo `char` o el tipo `wchar_t`, dependiendo de si se ha definido el símbolo `MBCS` o el símbolo `UNICODE` en el tiempo de compilación.  
  
 Un objeto `CString` conserva los datos de caracteres en un objeto `CStringData`. `CString` acepta cadenas de estilo C terminadas en `null`, pero no conserva el carácter `null` en los datos de caracteres almacenados. En su lugar, `CString` realiza un seguimiento de la longitud de la cadena. `CString` sí proporciona un terminador nulo cuando exporta una cadena de estilo C. Se puede insertar un elemento `null` en `CString`, pero esto podría generar resultados inesperados.  
  
 El siguiente conjunto de clases de cadenas puede usarse sin vincular una biblioteca MFC, con o sin compatibilidad con CRT: `CAtlString`, `CAtlStringA`, y `CAtlStringW`.  
  
 `CString` se usa en objetos nativos. En los proyectos de código administrado (C++/CLI), use `System::String`.  
  
 Para agregar más capacidades de las que `CString`, `CStringA` o `CStringW` ofrecen actualmente, conviene crear una subclase de `CStringT` que contenga las características extra.  
  
 El siguiente código muestra cómo crear una `CString` e imprimirla en una salida estándar:  
  
```cpp  
#include <atlstr.h>  
  
int main() {  
    CString aCString = CString(_T("A string"));  
    _tprintf(_T("%s"), (LPCTSTR) aCString);  
}  
```  
  
## <a name="in-this-section"></a>En esta sección  
 [Operaciones básicas de CString](../atl-mfc-shared/basic-cstring-operations.md)  
 Se describen las operaciones básicas de `CString`, por ejemplo, cómo crear objetos a partir de cadenas literales de C, cómo acceder a caracteres individuales de una `CString`, cómo concatenar dos objetos y cómo comparar objetos `CString`.  
  
 [Administración de datos de cadena](../atl-mfc-shared/string-data-management.md)  
 Se aborda el uso de Unicode y MBCS con `CString`.  
  
 [Semántica de CString](../atl-mfc-shared/cstring-semantics.md)  
 Se explica el uso de objetos `CString`.  
  
 [Operaciones de CString relacionadas con cadenas de estilo C](../atl-mfc-shared/cstring-operations-relating-to-c-style-strings.md)  
 Se describe cómo manipular el contenido de un objeto `CString` como una cadena terminada en un valor nulo de estilo C.  
  
 [Asignación y liberación de memoria para un BSTR](../atl-mfc-shared/allocating-and-releasing-memory-for-a-bstr.md)  
 Se explica el uso de memoria en relación con un `BSTR` y objetos COM.  
  
 [Limpieza de excepciones de CString](../atl-mfc-shared/cstring-exception-cleanup.md)  
 Se explica que la limpieza expresa en MFC 3.0 y en versiones posteriores ya no es necesaria.  
  
 [Paso de argumentos de CString](../atl-mfc-shared/cstring-argument-passing.md)  
 Se detalla cómo pasar objetos CString a funciones y cómo obtener objetos `CString` de las funciones.  
  
 [Compatibilidad con Unicode y con el juego de caracteres multibyte (MBCS)](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)  
 Se centra en cómo MFC permite el uso de Unicode y MBCS.  
  
## <a name="reference"></a>Referencia  
 [CStringT](../atl-mfc-shared/reference/cstringt-class.md)  
 Contiene información de referencia sobre la clase `CStringT`.  
  
 [CSimpleStringT (clase)](../atl-mfc-shared/reference/csimplestringt-class.md)  
 Contiene información de referencia sobre la clase `CSimpleStringT`.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Cadenas (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)  
 Contiene vínculos a temas en los que se describen las diversas formas de administrar datos de cadena.  
  
 [Cadenas (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)

