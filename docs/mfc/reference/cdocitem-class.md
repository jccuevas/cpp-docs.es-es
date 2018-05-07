---
title: Clase CDocItem | Documentos de Microsoft
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
ms.openlocfilehash: 724e5017f51a3527e2ad81bcf707179053cc3e88
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="cdocitem-class"></a>Clase CDocItem
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
 `CDocItem` los objetos se utilizan para representar elementos OLE en documentos de cliente y servidor.  
  
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
 Un puntero al documento que contiene el elemento; **NULL**, si el elemento no forma parte de un documento.  
  
### <a name="remarks"></a>Comentarios  
 Esta función se reemplaza en las clases derivadas [COleClientItem](../../mfc/reference/coleclientitem-class.md) y [COleServerItem](../../mfc/reference/coleserveritem-class.md), devuelve un puntero a cualquiera una [COleDocument](../../mfc/reference/coledocument-class.md), [ COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md), o un [COleServerDoc](../../mfc/reference/coleserverdoc-class.md) objeto.  
  
##  <a name="isblank"></a>  CDocItem::IsBlank  
 Llamado por el marco de trabajo cuando se produce la serialización predeterminada.  
  
```  
virtual BOOL IsBlank() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el elemento no contiene información; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, `CDocItem` objetos no están en blanco. [COleClientItem](../../mfc/reference/coleclientitem-class.md) objetos a veces son en blanco porque derivan directamente de `CDocItem`. Sin embargo, [COleServerItem](../../mfc/reference/coleserveritem-class.md) objetos siempre están en blanco. De forma predeterminada, las aplicaciones de OLE que contienen `COleClientItem` objetos que no tienen ningún x o y extensión se serializan. Esto se realiza mediante la devolución **TRUE** en las invalidaciones de `IsBlank` cuando el elemento no tiene ningún x o y extensión.  
  
 Reemplace esta función si desea implementar otras acciones durante la serialización.  
  
## <a name="see-also"></a>Vea también  
 [CCmdTarget (clase)](../../mfc/reference/ccmdtarget-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [COleDocument (clase)](../../mfc/reference/coledocument-class.md)   
 [Clase COleServerItem](../../mfc/reference/coleserveritem-class.md)   
 [COleClientItem (clase)](../../mfc/reference/coleclientitem-class.md)
