---
title: '&lt;value&gt; (Visual C++)'
ms.date: 11/04/2016
f1_keywords:
- value
- <value>
helpviewer_keywords:
- value C++ XML tag
- <value> C++ XML tag
ms.assetid: 0ba0a0d5-bcd7-4862-a169-83f2721ad80e
ms.openlocfilehash: 84a19c96e3e7024dbb891c6bde91646d4731b2be
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50599295"
---
# <a name="ltvaluegt-visual-c"></a>&lt;value&gt; (Visual C++)

La etiqueta \<value> permite describir una propiedad y los métodos de descriptor de acceso de propiedad. Tenga en cuenta que cuando agrega una propiedad mediante un asistente de código en el entorno de desarrollo integrado de Visual Studio, agregará una etiqueta [\<summary>](../ide/summary-visual-cpp.md) para la propiedad nueva. Después, debe agregar manualmente una etiqueta \<value> para describir el valor que representa esa propiedad.

## <a name="syntax"></a>Sintaxis

```
<value>property-description</value>
```

#### <a name="parameters"></a>Parámetros

*property-description*<br/>
Una descripción de la propiedad.

## <a name="remarks"></a>Comentarios

Compile con [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) para procesar los comentarios de documentación a un archivo.

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

[Documentación de XML](../ide/xml-documentation-visual-cpp.md)