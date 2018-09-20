---
title: Contextos de atributo | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++/CLI], contexts
ms.assetid: 3086351f-77a8-4048-99e9-3b6b041b9437
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f34fb2a019e922f7eed3a430e62be272f9d57dce
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46427295"
---
# <a name="attribute-contexts"></a>Atributos de contexto
Atributos de C++ se pueden describir mediante los cuatro campos básicos: el destino se puede aplicar a (**se aplica a**), si son repetibles o no (**repetible**), el requiere la presencia de otros atributos ( **Atributos requeridos**) y las incompatibilidades con otros atributos (**atributos no válidos**). Estos campos se muestran en una tabla que aparece en el tema de referencia de cada atributo. Cada uno de estos campos se describe a continuación.
  
## <a name="applies-to"></a>Se aplica a

Este campo describe los diferentes elementos del lenguaje C++ que son destinos válidos para el atributo especificado. Por ejemplo, si un atributo especifica "class" en la **se aplica a** campo, esto indica que el atributo solo puede aplicarse a una clase de C++ válida. Si el atributo se aplica a una función miembro de una clase, se produciría un error de sintaxis.
  
Para obtener más información, consulte [atributos por uso](../windows/attributes-by-usage.md).
  
## <a name="repeatable"></a>Reiterativo

Este campo indica si el atributo puede aplicarse varias veces en el mismo destino. La mayoría de los atributos no son repetibles.
  
## <a name="required-attributes"></a>Atributos requeridos

Este campo muestra otros atributos que deben estar presentes (que es, se aplican al mismo destino) para el atributo especificado funcionar correctamente. Es raro que un atributo para que todas las entradas para este campo.
  
## <a name="invalid-attributes"></a>Atributos no válidos

Este campo muestra otros atributos que no son compatibles con el atributo especificado. Es raro que un atributo para que todas las entradas para este campo.
  
## <a name="see-also"></a>Vea también

[Referencia de atributos de C++](../windows/cpp-attributes-reference.md)