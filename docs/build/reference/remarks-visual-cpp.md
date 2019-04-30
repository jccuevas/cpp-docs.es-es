---
title: '&lt;remarks > (comentarios de documentación de C++)'
ms.date: 11/04/2016
f1_keywords:
- remarks
- <remarks>
helpviewer_keywords:
- <remarks> C++ XML tag
- remarks C++ XML tag
ms.assetid: c820083b-3192-40ab-9ec8-1472c55b4247
ms.openlocfilehash: 0d0c63d55de80f498498a6873dacb5e83fc956b7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62319166"
---
# <a name="ltremarksgt"></a>&lt;remarks&gt;

La etiqueta \<remarks> se usa para agregar información sobre un tipo y complementa la información especificada con [\<summary>](summary-visual-cpp.md). Esta información se muestra en la ventana [Examinador de objetos](/visualstudio/ide/viewing-the-structure-of-code) y en el informe web de comentario de código.

## <a name="syntax"></a>Sintaxis

```
<remarks>description</remarks>
```

#### <a name="parameters"></a>Parámetros

*description*<br/>
Descripción del miembro.

## <a name="remarks"></a>Comentarios

Compile con [/doc](doc-process-documentation-comments-c-cpp.md) para procesar los comentarios de documentación a un archivo.

## <a name="example"></a>Ejemplo

```
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
