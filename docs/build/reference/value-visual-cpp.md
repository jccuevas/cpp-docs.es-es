---
title: '> de valor &lt;C++ (comentarios de documentación)'
ms.date: 11/04/2016
f1_keywords:
- value
- <value>
helpviewer_keywords:
- value C++ XML tag
- <value> C++ XML tag
ms.assetid: 0ba0a0d5-bcd7-4862-a169-83f2721ad80e
ms.openlocfilehash: de84d1faca59a6c8e4f82fba3605cbd54a05bd2e
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988595"
---
# <a name="ltvaluegt"></a>&lt;valor&gt;

La etiqueta \<value> permite describir una propiedad y los métodos de descriptor de acceso de propiedad. Tenga en cuenta que cuando agrega una propiedad mediante un asistente de código en el entorno de desarrollo integrado de Visual Studio, agregará una etiqueta [\<summary>](summary-visual-cpp.md) para la propiedad nueva. Después, debe agregar manualmente una etiqueta \<value> para describir el valor que representa esa propiedad.

## <a name="syntax"></a>Sintaxis

```
<value>property-description</value>
```

#### <a name="parameters"></a>Parameters

*property-description*<br/>
Una descripción de la propiedad.

## <a name="remarks"></a>Notas

Compile con el parámetro [/doc](doc-process-documentation-comments-c-cpp.md) para procesar los comentarios de documentación y generar un archivo con ellos.

## <a name="example"></a>Ejemplo

```cpp
// xml_value_tag.cpp
// compile with: /LD /clr /doc
// post-build command: xdcmake xml_value_tag.dll
using namespace System;
/// Text for class Employee.
public ref class Employee {
private:
   String ^ name;
   /// <value>Name accesses the value of the name data member</value>
public:
   property String ^ Name {
      String ^ get() {
         return name;
      }
      void set(String ^ i) {
         name = i;
      }
   }
};
```

## <a name="see-also"></a>Vea también

[Documentación de XML](xml-documentation-visual-cpp.md)
