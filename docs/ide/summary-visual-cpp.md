---
title: '&lt;summary&gt; (Visual C++)'
ms.date: 11/04/2016
f1_keywords:
- <summary>
- summary
helpviewer_keywords:
- <summary> C++ XML tag
- summary C++ XML tag
ms.assetid: cdeeefbb-1339-45d6-9002-10042a9a2726
ms.openlocfilehash: 08d03d19355b89fa3c59ce5bede514d3ffa9b55b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50509110"
---
# <a name="ltsummarygt-visual-c"></a>&lt;summary&gt; (Visual C++)

La etiqueta \<summary> debe usarse para describir un tipo o un miembro de tipo. Use [\<remarks>](../ide/remarks-visual-cpp.md) para agregar información adicional a una descripción de tipo.

## <a name="syntax"></a>Sintaxis

```
<summary>description</summary>
```

#### <a name="parameters"></a>Parámetros

*description*<br/>
Resumen del objeto.

## <a name="remarks"></a>Comentarios

El texto de la etiqueta \<summary> es la única fuente de información sobre el tipo en IntelliSense y también se muestra en la ventana [Examinador de objetos](/visualstudio/ide/viewing-the-structure-of-code) y el informe web de comentario de código.

Compile con [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) para procesar los comentarios de documentación a un archivo.

## <a name="example"></a>Ejemplo

```
// xml_summary_tag.cpp
// compile with: /LD /clr /doc
// post-build command: xdcmake xml_summary_tag.dll

/// Text for class MyClass.
public ref class MyClass {
public:
   /// <summary>MyMethod is a method in the MyClass class.
   /// <para>Here's how you could make a second paragraph in a description. <see cref="System::Console::WriteLine"/> for information about output statements.</para>
   /// <seealso cref="MyClass::MyMethod2"/>
   /// </summary>
   void MyMethod(int Int1) {}

   /// text
   void MyMethod2() {}
};
```

## <a name="see-also"></a>Vea también

[Documentación de XML](../ide/xml-documentation-visual-cpp.md)