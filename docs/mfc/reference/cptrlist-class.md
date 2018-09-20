---
title: CPtrList (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CPtrList
dev_langs:
- C++
helpviewer_keywords:
- lists, generic
- CPtrList class [MFC]
- generic lists
ms.assetid: 4139a09c-4338-4f42-9eea-51336120b43c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 97eeeaaa2eea237eebda4f945f2c810268f406cd
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46384967"
---
# <a name="cptrlist-class"></a>CPtrList (clase)

Admite listas de punteros void.

## <a name="syntax"></a>Sintaxis

```
class CPtrList : public CObject
```

## <a name="members"></a>Miembros

Las funciones miembro de `CPtrList` son similares a las funciones miembro de clase [CObList](../../mfc/reference/coblist-class.md). Debido a esta similitud, puede utilizar la documentación de referencia de `CObList` para obtener información específica de la función miembro. Siempre que vea un `CObject` puntero como un parámetro de función o el valor devuelto, utilice un puntero a **void**.

`CObject*& CObList::GetHead() const;`

por ejemplo, se traduce en

`void*& CPtrList::GetHead() const;`

## <a name="remarks"></a>Comentarios

`CPtrList` incorpora la macro IMPLEMENT_DYNAMIC para admitir el acceso a los tipos de tiempo de ejecución y el volcado en un `CDumpContext` objeto. Si se necesita un volcado de elementos de lista de punteros individuales, se debe establecer la profundidad del contexto de volcado en 1 o un valor superior.

Las listas de punteros no se pueden serializar.

Cuando se elimina un objeto `CPtrList`, o cuando se quitan sus elementos, solo se quitan los punteros, no las entidades a las que hacen referencia.

Para obtener más información sobre el uso de `CPtrList`, consulte el artículo [colecciones](../../mfc/collections.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CPtrList`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcoll.h

## <a name="see-also"></a>Vea también

[CObject (clase)](../../mfc/reference/cobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CObList (clase)](../../mfc/reference/coblist-class.md)
