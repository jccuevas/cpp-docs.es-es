---
title: Clase CDocItem | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDocItem
- AFXOLE/CDocItem
- AFXOLE/CDocItem::GetDocument
- AFXOLE/CDocItem::IsBlank
dev_langs:
- C++
helpviewer_keywords:
- items, document
- document items
- server documents, document items
- CDocItem class
- container document items
- client document items
- OLE documents, items
- server documents
ms.assetid: 84fb8610-a4c8-4211-adc0-e70e8d002c11
caps.latest.revision: 22
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 1ade88aa562180d5c3a6a7afe3fe26943a5d811d
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

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
|[CDocItem::IsBlank](#isblank)|Determina si el elemento contiene toda la información.|  
  
## <a name="remarks"></a>Comentarios  
 `CDocItem`los objetos se utilizan para representar elementos OLE en documentos de cliente y servidor.  
  
 Para obtener más información, vea el artículo [contenedores: implementar un contenedor](../../mfc/containers-implementing-a-container.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CDocItem`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxole.h  
  
##  <a name="getdocument"></a>CDocItem::GetDocument  
 Llame a esta función para obtener el documento que contiene el elemento.  
  
```  
CDocument* GetDocument() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al documento que contiene el elemento; **NULL**, si el elemento no es parte de un documento.  
  
### <a name="remarks"></a>Comentarios  
 Esta función se reemplaza en las clases derivadas [COleClientItem](../../mfc/reference/coleclientitem-class.md) y [COleServerItem](../../mfc/reference/coleserveritem-class.md), devuelve un puntero a uno un [COleDocument](../../mfc/reference/coledocument-class.md), [COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md), o un [COleServerDoc](../../mfc/reference/coleserverdoc-class.md) objeto.  
  
##  <a name="isblank"></a>CDocItem::IsBlank  
 Llamado por el marco de trabajo cuando se produce la serialización predeterminada.  
  
```  
virtual BOOL IsBlank() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el elemento no contiene información; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, `CDocItem` objetos no están en blanco. [COleClientItem](../../mfc/reference/coleclientitem-class.md) objetos a veces están en blanco porque se derivan directamente de `CDocItem`. Sin embargo, [COleServerItem](../../mfc/reference/coleserveritem-class.md) objetos siempre están en blanco. De forma predeterminada, que contiene las aplicaciones OLE `COleClientItem` objetos que no tienen ningún x o y extensión se serializan. Esto se realiza mediante la devolución de **TRUE** desde un reemplazo de `IsBlank` cuando el elemento no tiene ningún x o y extensión.  
  
 Reemplace esta función si desea implementar otras acciones durante la serialización.  
  
## <a name="see-also"></a>Vea también  
 [CCmdTarget (clase)](../../mfc/reference/ccmdtarget-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [COleDocument (clase)](../../mfc/reference/coledocument-class.md)   
 [Clase COleServerItem](../../mfc/reference/coleserveritem-class.md)   
 [Clase de COleClientItem](../../mfc/reference/coleclientitem-class.md)

