---
title: '&lt;valor > (comentarios de documentación de C++)'
ms.date: 11/04/2016
f1_keywords:
- value
- <value>
helpviewer_keywords:
- value C++ XML tag
- <value> C++ XML tag
ms.assetid: 0ba0a0d5-bcd7-4862-a169-83f2721ad80e
ms.openlocfilehash: c0863b41791254992d16d373328ff6c8a5d6f94f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62317034"
---
# <a name="ltvaluegt"></a>&lt;value&gt;

La etiqueta \<value> permite describir una propiedad y los métodos de descriptor de acceso de propiedad. Tenga en cuenta que cuando agrega una propiedad mediante un asistente de código en el entorno de desarrollo integrado de Visual Studio, agregará una etiqueta [\<summary>](summary-visual-cpp.md) para la propiedad nueva. Después, debe agregar manualmente una etiqueta \<value> para describir el valor que representa esa propiedad.

## <a name="syntax"></a>Sintaxis

```
<value>property-description</value>
```

#### <a name="parameters"></a>Parámetros

*property-description*<br/>
Una descripción de la propiedad.

## <a name="remarks"></a>Comentarios

Compile con [/doc](doc-process-documentation-comments-c-cpp.md) para procesar los comentarios de documentación a un archivo.

## <a name="example"></a>Ejemplo

```
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
