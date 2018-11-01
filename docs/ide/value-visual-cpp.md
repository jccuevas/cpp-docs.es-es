---
title: '&lt;value&gt; (Visual C++) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- value
- <value>
dev_langs:
- C++
helpviewer_keywords:
- value C++ XML tag
- <value> C++ XML tag
ms.assetid: 0ba0a0d5-bcd7-4862-a169-83f2721ad80e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9bd811080e3a5587056d67a45fce345b0a2b4d37
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46419807"
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