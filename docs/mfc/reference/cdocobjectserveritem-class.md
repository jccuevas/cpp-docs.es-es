---
title: Clase CDocObjectServerItem | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDocObjectServerItem
dev_langs:
- C++
helpviewer_keywords:
- document object server
- CDocObjectServerItem class
- servers [C++], ActiveX documents
- docobject server
- servers [C++], doc objects
- ActiveX documents [C++], document server
ms.assetid: 530f7156-50c8-4806-9328-602c9133f622
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
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 06cf873512fbf43b729d9a70f185582a4e48cafc
ms.lasthandoff: 02/24/2017

---
# <a name="cdocobjectserveritem-class"></a>Clase CDocObjectServerItem
Implementa verbos de servidor OLE específicamente para servidores de DocObject.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CDocObjectServerItem : public COleServerItem  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="protected-constructors"></a>Constructores protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDocObjectServerItem::CDocObjectServerItem](#cdocobjectserveritem)|Construye un objeto `CDocObjectServerItem`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CDocObjectServerItem::GetDocument](#getdocument)|Recupera un puntero al documento que contiene el elemento.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CDocObjectServerItem::OnHide](#onhide)|Produce una excepción si el marco de trabajo intenta ocultar un elemento de DocObject.|  
|[CDocObjectServerItem::OnShow](#onshow)|Llamado por el marco de trabajo para realizar el DocObject elemento en el contexto activo. Si el elemento no es un objeto DocObject, llama a [COleServerItem::OnShow](../../mfc/reference/coleserveritem-class.md#onshow).|  
  
## <a name="remarks"></a>Comentarios  
 `CDocObjectServerItem`define las funciones miembro reemplazables: [OnHide](#onhide), [OnOpen](http://msdn.microsoft.com/en-us/7a9b1363-6ad8-4732-9959-4e35c07644fd), y [OnShow](#onshow).  
  
 Usar `CDocObjectServerItem`, asegurarse de que el [OnGetEmbeddedItem](../../mfc/reference/coleserverdoc-class.md#ongetembeddeditem) invalidar en la `COleServerDoc`-devuelve una nueva clase derivada `CDocObjectServerItem` objeto. Si necesita cambiar cualquier funcionalidad en el elemento, puede crear una nueva instancia de su propio `CDocObjectServerItem`-clase derivada.  
  
 Para obtener más información sobre DocObjects, consulte [CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md) y [COleCmdUI](../../mfc/reference/colecmdui-class.md) en el *referencia de MFC*. Consulte también [primeros pasos de Internet: documentos activos](../../mfc/active-documents-on-the-internet.md) y [documentos activos](../../mfc/active-documents-on-the-internet.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocItem](../../mfc/reference/cdocitem-class.md)  
  
 [COleServerItem](../../mfc/reference/coleserveritem-class.md)  
  
 `CDocObjectServerItem`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdocob.h  
  
##  <a name="a-namecdocobjectserveritema--cdocobjectserveritemcdocobjectserveritem"></a><a name="cdocobjectserveritem"></a>CDocObjectServerItem::CDocObjectServerItem  
 Construye un objeto `CDocObjectServerItem`.  
  
```  
CDocObjectServerItem(COleServerDoc* pServerDoc, BOOL bAutoDelete);
```  
  
### <a name="parameters"></a>Parámetros  
 `pServerDoc`  
 Un puntero al documento que contendrá el nuevo elemento de DocObject.  
  
 `bAutoDelete`  
 Indica si el objeto se puede eliminar cuando se suelta un vínculo a él. Establezca el argumento en **FALSE** si la `CDocObjectServerItem` objeto es una parte integral de los datos del documento. Establézcalo en **TRUE** si el objeto es una estructura secundaria utilizada para identificar un intervalo en los datos del documento que se pueden eliminar mediante el marco de trabajo.  
  
##  <a name="a-namegetdocumenta--cdocobjectserveritemgetdocument"></a><a name="getdocument"></a>CDocObjectServerItem::GetDocument  
 Recupera un puntero al documento que contiene el elemento.  
  
```  
COleServerDoc* GetDocument() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al documento que contiene el elemento; **NULL** si el elemento no forma parte de un documento.  
  
### <a name="remarks"></a>Comentarios  
 Esto permite el acceso al documento del servidor que se pasa como argumento a la [CDocObjectServerItem](#cdocobjectserveritem) constructor.  
  
##  <a name="a-nameonhidea--cdocobjectserveritemonhide"></a><a name="onhide"></a>CDocObjectServerItem::OnHide  
 Llamado por el marco para ocultar el elemento.  
  
```  
virtual void OnHide();
```  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada produce una excepción si el elemento es un objeto DocObject. No se puede ocultar un elemento de DocObject activo porque toma la vista entera. Debe desactivar el elemento DocObject para que desaparezca. Si el elemento no es un objeto DocObject, la implementación predeterminada llama [COleServerItem::OnHide](../../mfc/reference/coleserveritem-class.md#onhide).  
  
##  <a name="a-nameonshowa--cdocobjectserveritemonshow"></a><a name="onshow"></a>CDocObjectServerItem::OnShow  
 Llamado por el marco para indicar a la aplicación de servidor para hacer el DocObject elemento en el contexto activo.  
  
```  
virtual void OnShow();
```  
  
### <a name="remarks"></a>Comentarios  
 Si el elemento no es un objeto DocObject, la implementación predeterminada llama [COleServerItem::OnShow](../../mfc/reference/coleserveritem-class.md#onopen). Reemplace esta función si desea realizar el procesamiento al abrir un elemento de DocObject especial.  
  
## <a name="see-also"></a>Vea también  
 [Clase COleServerItem](../../mfc/reference/coleserveritem-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clase CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md)   
 [Clase COleDocObjectItem](../../mfc/reference/coledocobjectitem-class.md)

