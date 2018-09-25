---
title: '&lt;param&gt; (Visual C++) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- param
- <param>
dev_langs:
- C++
helpviewer_keywords:
- param C++ XML tag
- <param> C++ XML tag
ms.assetid: 66c1a1c3-4f98-4bcf-8c7d-9a40308982fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 94382cb1f2bab59fae6c397f8ad6dadee221c96b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46434848"
---
# <a name="ltparamgt-visual-c"></a>&lt;param&gt; (Visual C++)

La etiqueta \<param> debe usarse en el comentario de una declaración de método para describir uno de los parámetros del método.

## <a name="syntax"></a>Sintaxis

```
<param name='name'>description</param>
```

#### <a name="parameters"></a>Parámetros

*name*<br/>
Nombre de un parámetro de método.  Ponga el nombre entre comillas simples o dobles.  El compilador emite una advertencia si no encuentra `name`.

*description*<br/>
Descripción del parámetro.

## <a name="remarks"></a>Comentarios

El texto de la etiqueta \<param> se mostrará en IntelliSense, el [Examinador de objetos](/visualstudio/ide/viewing-the-structure-of-code) y en el informe web de comentario de código.

Compile con [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) para procesar los comentarios de documentación a un archivo.

## <a name="example"></a>Ejemplo

```cpp
// xml_param_tag.cpp
// compile with: /clr /doc /LD
// post-build command: xdcmake xml_param_tag.dll
/// Text for class MyClass.
public ref class MyClass {
   /// <param name="Int1">Used to indicate status.</param>
   void MyMethod(int Int1) {
   }
};
```

## <a name="see-also"></a>Vea también

[Documentación de XML](../ide/xml-documentation-visual-cpp.md)