---
title: CDocItem (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDocItem
- AFXOLE/CDocItem
- AFXOLE/CDocItem::GetDocument
- AFXOLE/CDocItem::IsBlank
dev_langs:
- C++
helpviewer_keywords:
- CDocItem [MFC], GetDocument
- CDocItem [MFC], IsBlank
ms.assetid: 84fb8610-a4c8-4211-adc0-e70e8d002c11
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 88c30418f886cd791a7119367c5ddbccc19003fa
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37335586"
---
# <a name="cdocitem-class"></a>CDocItem (clase)
La clase base para los elementos de documento, que son componentes de los datos de un documento.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CDocItem : public CCmdTarget  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDocItem::GetDocument](#getdocument)|Devuelve el documento que contiene el elemento.|  
|[CDocItem::IsBlank](#isblank)|Determina si el elemento contiene toda la información.|  
  
## <a name="remarks"></a>Comentarios  
 `CDocItem` los objetos se utilizan para representar los elementos OLE en documentos de cliente y servidor.  
  
 Para obtener más información, vea el artículo [contenedores: implementar un contenedor](../../mfc/containers-implementing-a-container.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CDocItem`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxole.h  
  
##  <a name="getdocument"></a>  CDocItem::GetDocument  
 Llame a esta función para obtener el documento que contiene el elemento.  
  
```  
CDocument* GetDocument() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al documento que contiene el elemento; Es NULL, si el elemento no forma parte de un documento.  
  
### <a name="remarks"></a>Comentarios  
 Esta función se reemplaza en las clases derivadas [COleClientItem](../../mfc/reference/coleclientitem-class.md) y [COleServerItem](../../mfc/reference/coleserveritem-class.md), devuelve un puntero a la ya sea un [COleDocument](../../mfc/reference/coledocument-class.md), un [ COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md), o un [COleServerDoc](../../mfc/reference/coleserverdoc-class.md) objeto.  
  
##  <a name="isblank"></a>  CDocItem::IsBlank  
 Lo llama el marco de trabajo cuando se produce la serialización predeterminada.  
  
```  
virtual BOOL IsBlank() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el elemento no contiene ninguna información; en caso contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, `CDocItem` objetos no están en blanco. [COleClientItem](../../mfc/reference/coleclientitem-class.md) objetos a veces están en blanco, dado que proceden directamente de `CDocItem`. Sin embargo, [COleServerItem](../../mfc/reference/coleserveritem-class.md) objetos siempre están en blanco. De forma predeterminada, que contiene las aplicaciones OLE `COleClientItem` objetos que no tienen ningún x o y extensión se serializan. Esto se hace devolviendo TRUE desde un reemplazo de `IsBlank` cuando el elemento no tiene ningún x o y extensión.  
  
 Reemplace esta función si desea implementar otras acciones durante la serialización.  
  
## <a name="see-also"></a>Vea también  
 [CCmdTarget (clase)](../../mfc/reference/ccmdtarget-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [COleDocument (clase)](../../mfc/reference/coledocument-class.md)   
 [COleServerItem (clase)](../../mfc/reference/coleserveritem-class.md)   
 [COleClientItem (clase)](../../mfc/reference/coleclientitem-class.md)
