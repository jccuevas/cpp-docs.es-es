---
title: Clases ref de plantilla (C++/CX)
ms.date: 01/22/2017
ms.assetid: a24d5f45-8dbb-4540-958f-c76c90d8ed93
ms.openlocfilehash: 4398cc2c545a57277289a6aa41fc4664d9734eed
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62396042"
---
# <a name="template-ref-classes-ccx"></a>Clases ref de plantilla (C++/CX)

Las plantillas de C++ no se publican para metadatos y, por consiguiente, no pueden tener accesibilidad pública ni protegida en tu programa. Puedes, por supuesto, utilizar las plantillas de C++ estándar internamente en tu programa. Además, puedes definir una clase ref privada como plantilla y puedes declarar una clase ref de plantilla especializada de forma explícita como miembro privado de una clase ref pública.

## <a name="authoring-ref-class-templates"></a>Crear plantillas de clase ref

En el ejemplo siguiente se muestra cómo declarar una clase ref privada como plantilla y también cómo declarar una plantilla de C++ estándar, y cómo declarar ambas como miembros de una clase ref pública. Tenga en cuenta que el estándar C++ se puede especializar la plantilla de un tipo en tiempo de ejecución de Windows, en este caso un Platform:: String ^.

[!code-cpp[cx_templates#01](../cppcx/codesnippet/CPP/templatedemo/class1.h#01)]

## <a name="see-also"></a>Vea también

[Sistema de tipos (C++/CX)](../cppcx/type-system-c-cx.md)<br/>
[Referencia del lenguaje de Visual C++](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Referencia de espacios de nombres](../cppcx/namespaces-reference-c-cx.md)
