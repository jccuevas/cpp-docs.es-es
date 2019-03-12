---
title: '&lt;list&gt; (Visual C++)'
ms.date: 11/04/2016
f1_keywords:
- list
- <list>
helpviewer_keywords:
- list C++ XML tag
- <list> C++ XML tag
ms.assetid: c792a10b-0451-422c-9aa0-604116e69d64
ms.openlocfilehash: 015647cd381ba4dc0c099b322e3c5870246c9fc2
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57751349"
---
# <a name="ltlistgt-visual-c"></a>&lt;list&gt; (Visual C++)

El bloque \<listheader> se usa para definir la fila de encabezado de una tabla o de una lista de definiciones. Cuando se define una tabla, solo es necesario suministrar una entrada para un término en el encabezado.

## <a name="syntax"></a>Sintaxis

```
<list type="bullet" | "number" | "table">
   <listheader>
      <term>term</term>
      <description>description</description>
   </listheader>
   <item>
      <term>term</term>
      <description>description</description>
   </item>
</list>
```

#### <a name="parameters"></a>Parámetros

*term*<br/>
Término que se define en `description`.

*description*<br/>
Elemento de una lista numerada o con viñetas, o definición de un `term`.

## <a name="remarks"></a>Comentarios

Cada elemento de la lista se especifica con un bloque \<item>. Cuando se crea una lista de definiciones, se deberán especificar tanto `term` como `description`. En cambio, para una tabla, lista con viñetas o lista numerada, solo es necesario suministrar una entrada para `description`.

Una lista o una tabla pueden tener tantos bloques \<item> como sean necesarios.

Compile con [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) para procesar los comentarios de documentación a un archivo.

## <a name="example"></a>Ejemplo

```cpp
// xml_list_tag.cpp
// compile with: /doc /LD
// post-build command: xdcmake xml_list_tag.dll
/// <remarks>Here is an example of a bulleted list:
/// <list type="bullet">
/// <item>
/// <description>Item 1.</description>
/// </item>
/// <item>
/// <description>Item 2.</description>
/// </item>
/// </list>
/// </remarks>
class MyClass {};
```

## <a name="see-also"></a>Vea también

[Documentación de XML](../ide/xml-documentation-visual-cpp.md)
