---
title: '&lt;Comentarios > (C++ comentarios de documentación)'
ms.date: 11/04/2016
f1_keywords:
- remarks
- <remarks>
helpviewer_keywords:
- <remarks> C++ XML tag
- remarks C++ XML tag
ms.assetid: c820083b-3192-40ab-9ec8-1472c55b4247
ms.openlocfilehash: 096280526b12feff33377a705f7c03548a1f0f13
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988652"
---
# <a name="ltremarksgt"></a>&lt;remarks&gt;

La etiqueta \<remarks> se usa para agregar información sobre un tipo y complementa la información especificada con [\<summary>](summary-visual-cpp.md). Esta información se muestra en la ventana [Examinador de objetos](/visualstudio/ide/viewing-the-structure-of-code) y en el informe web de comentario de código.

## <a name="syntax"></a>Sintaxis

```
<remarks>description</remarks>
```

#### <a name="parameters"></a>Parameters

*description*<br/>
Descripción del miembro.

## <a name="remarks"></a>Notas

Compile con el parámetro [/doc](doc-process-documentation-comments-c-cpp.md) para procesar los comentarios de documentación y generar un archivo con ellos.

## <a name="example"></a>Ejemplo

```cpp
// xml_remarks_tag.cpp
// compile with: /LD /clr /doc
// post-build command: xdcmake xml_remarks_tag.dll

using namespace System;

/// <summary>
/// You may have some primary information about this class.
/// </summary>
/// <remarks>
/// You may have some additional information about this class.
/// </remarks>
public ref class MyClass {};
```

## <a name="see-also"></a>Vea también

[Documentación de XML](xml-documentation-visual-cpp.md)
