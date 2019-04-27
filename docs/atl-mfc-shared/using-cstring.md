---
title: Uso de CString
ms.date: 06/18/2018
helpviewer_keywords:
- CString objects, C++ string manipulation
- CString objects, reference counting
- CString class (Visual C++)
ms.assetid: ed018aaf-8b10-46f9-828c-f9c092dc7609
ms.openlocfilehash: a84ae21b60d87971cb2f7b758dd369b4078607e6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62199214"
---
# <a name="using-cstring"></a>Uso de CString

En los temas de esta sección se describe cómo programar con `CString`. Para obtener documentación de referencia sobre la `CString` de clases, consulte la documentación de [CStringT](../atl-mfc-shared/reference/cstringt-class.md).

Para usar `CString`, incluya el encabezado `atlstr.h`.

El `CString`, `CStringA`, y `CStringW` clases son especializaciones de una plantilla de clase llamado [CStringT](../atl-mfc-shared/reference/cstringt-class.md) según el tipo de datos de caracteres que admiten.

Un `CStringW` objeto contiene la **wchar_t** escriba y admite cadenas Unicode. Un `CStringA` objeto contiene la **char** tipo y cadenas de es compatible con un solo byte y multibyte (MBCS). Un `CString` objeto es compatible con la **char** tipo o el `wchar_t` tipo, dependiendo de si se ha definido el símbolo MBCS o el símbolo UNICODE en tiempo de compilación.

Un objeto `CString` conserva los datos de caracteres en un objeto `CStringData`. `CString` acepta cadenas de estilo C terminada en NULL. `CString` realiza un seguimiento de la cadena de longitud para un rendimiento más rápido, pero también conserva el carácter nulo en los datos de caracteres almacenados para admitir la conversión a LPCWSTR. `CString` incluye el terminador nulo cuando exporta una cadena de estilo C. Se puede insertar un valor NULL en otras ubicaciones en un `CString`, pero pueden producir resultados inesperados.

Se puede usar el siguiente conjunto de clases de cadenas sin vincular una biblioteca MFC, con o sin compatibilidad con CRT: `CAtlString`, `CAtlStringA`, y `CAtlStringW`.

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

[Operaciones básicas de CString](../atl-mfc-shared/basic-cstring-operations.md)<br/>
Se describen las operaciones básicas de `CString`, por ejemplo, cómo crear objetos a partir de cadenas literales de C, cómo acceder a caracteres individuales de una `CString`, cómo concatenar dos objetos y cómo comparar objetos `CString`.

[Administración de datos de cadena](../atl-mfc-shared/string-data-management.md)<br/>
Se aborda el uso de Unicode y MBCS con `CString`.

[Semántica de CString](../atl-mfc-shared/cstring-semantics.md)<br/>
Se explica el uso de objetos `CString`.

[Operaciones de CString relacionadas con cadenas de estilo C](../atl-mfc-shared/cstring-operations-relating-to-c-style-strings.md)<br/>
Se describe cómo manipular el contenido de un objeto `CString` como una cadena terminada en un valor nulo de estilo C.

[Asignación y liberación de memoria para un BSTR](../atl-mfc-shared/allocating-and-releasing-memory-for-a-bstr.md)<br/>
Describe el uso de memoria para un objeto COM y BSTR.

[Limpieza de excepciones de CString](../atl-mfc-shared/cstring-exception-cleanup.md)<br/>
Se explica que la limpieza expresa en MFC 3.0 y en versiones posteriores ya no es necesaria.

[Paso de argumentos de CString](../atl-mfc-shared/cstring-argument-passing.md)<br/>
Se detalla cómo pasar objetos CString a funciones y cómo obtener objetos `CString` de las funciones.

[Compatibilidad con Unicode y con el juego de caracteres multibyte (MBCS)](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)<br/>
Se centra en cómo MFC permite el uso de Unicode y MBCS.

## <a name="reference"></a>Referencia

[CStringT](../atl-mfc-shared/reference/cstringt-class.md)<br/>
Contiene información de referencia sobre la clase `CStringT`.

[CSimpleStringT (clase)](../atl-mfc-shared/reference/csimplestringt-class.md)<br/>
Contiene información de referencia sobre la clase `CSimpleStringT`.

## <a name="related-sections"></a>Secciones relacionadas

[Cadenas (ATL y MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
Contiene vínculos a temas en los que se describen las diversas formas de administrar datos de cadena.

[Cadenas (ATL y MFC)](../atl-mfc-shared/strings-atl-mfc.md)
