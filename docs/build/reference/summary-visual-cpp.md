---
title: '> de Resumen deC++ &lt;(comentarios de documentación)'
ms.date: 11/04/2016
f1_keywords:
- <summary>
- summary
helpviewer_keywords:
- <summary> C++ XML tag
- summary C++ XML tag
ms.assetid: cdeeefbb-1339-45d6-9002-10042a9a2726
ms.openlocfilehash: 0620273f24573539897809b7892d46ad49b7aa57
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988580"
---
# <a name="ltsummarygt"></a>&lt;summary&gt;

La etiqueta \<summary> debe usarse para describir un tipo o un miembro de tipo. Use [\<remarks>](remarks-visual-cpp.md) para agregar información adicional a una descripción de tipo.

## <a name="syntax"></a>Sintaxis

```
<summary>description</summary>
```

#### <a name="parameters"></a>Parameters

*description*<br/>
Resumen del objeto.

## <a name="remarks"></a>Notas

El texto de la etiqueta \<summary> es la única fuente de información sobre el tipo en IntelliSense y también se muestra en la ventana [Examinador de objetos](/visualstudio/ide/viewing-the-structure-of-code) y el informe web de comentario de código.

Compile con el parámetro [/doc](doc-process-documentation-comments-c-cpp.md) para procesar los comentarios de documentación y generar un archivo con ellos.

## <a name="example"></a>Ejemplo

```cpp
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

[Documentación de XML](xml-documentation-visual-cpp.md)
