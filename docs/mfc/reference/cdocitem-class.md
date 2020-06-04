---
title: CDocItem (clase)
ms.date: 11/04/2016
f1_keywords:
- CDocItem
- AFXOLE/CDocItem
- AFXOLE/CDocItem::GetDocument
- AFXOLE/CDocItem::IsBlank
helpviewer_keywords:
- CDocItem [MFC], GetDocument
- CDocItem [MFC], IsBlank
ms.assetid: 84fb8610-a4c8-4211-adc0-e70e8d002c11
ms.openlocfilehash: 438bc2a03239946dbfca53d5f2989c731b682ab0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375618"
---
# <a name="cdocitem-class"></a>CDocItem (clase)

La clase base para los elementos de documento, que son componentes de los datos de un documento.

## <a name="syntax"></a>Sintaxis

```
class CDocItem : public CCmdTarget
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDocItem::GetDocument](#getdocument)|Devuelve el documento que contiene el elemento.|
|[CDocItem::IsBlank](#isblank)|Determina si el elemento contiene información.|

## <a name="remarks"></a>Observaciones

`CDocItem`los objetos se utilizan para representar elementos OLE en documentos de cliente y servidor.

Para obtener más información, vea el artículo [Contenedores: implementar un contenedor](../../mfc/containers-implementing-a-container.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CDocItem`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxole.h

## <a name="cdocitemgetdocument"></a><a name="getdocument"></a>CDocItem::GetDocument

Llame a esta función para obtener el documento que contiene el elemento.

```
CDocument* GetDocument() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero al documento que contiene el elemento; NULL, si el elemento no forma parte de un documento.

### <a name="remarks"></a>Observaciones

Esta función se reemplaza en las clases derivadas [COleClientItem](../../mfc/reference/coleclientitem-class.md) y [COleServerItem](../../mfc/reference/coleserveritem-class.md), devolviendo un puntero a un [COleDocument](../../mfc/reference/coledocument-class.md), un [COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md), o un [COleServerDoc](../../mfc/reference/coleserverdoc-class.md) objeto.

## <a name="cdocitemisblank"></a><a name="isblank"></a>CDocItem::IsBlank

Llamado por el marco de trabajo cuando se produce la serialización predeterminada.

```
virtual BOOL IsBlank() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el elemento no contiene información; de lo contrario 0.

### <a name="remarks"></a>Observaciones

De forma `CDocItem` predeterminada, los objetos no están en blanco. [COleClientItem](../../mfc/reference/coleclientitem-class.md) objetos a veces `CDocItem`están en blanco porque derivan directamente de . Sin embargo, [COleServerItem](../../mfc/reference/coleserveritem-class.md) objetos siempre están en blanco. De forma predeterminada, `COleClientItem` se serializan las aplicaciones OLE que contienen objetos que no tienen ninguna extensión x o y. Esto se hace devolviendo TRUE `IsBlank` de una invalidación de cuando el elemento no tiene ninguna extensión x o y.

Invalide esta función si desea implementar otras acciones durante la serialización.

## <a name="see-also"></a>Consulte también

[CCmdTarget (clase)](../../mfc/reference/ccmdtarget-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[COleDocument (Clase)](../../mfc/reference/coledocument-class.md)<br/>
[COleServerItem (clase)](../../mfc/reference/coleserveritem-class.md)<br/>
[Clase COleClientItem](../../mfc/reference/coleclientitem-class.md)
