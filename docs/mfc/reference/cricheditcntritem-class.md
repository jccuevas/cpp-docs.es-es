---
title: Clase CRichEditCntrItem | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CRichEditCntrItem
- AFXRICH/CRichEditCntrItem
- AFXRICH/CRichEditCntrItem::CRichEditCntrItem
- AFXRICH/CRichEditCntrItem::SyncToRichEditObject
dev_langs:
- C++
helpviewer_keywords:
- CRichEditCntrItem class
- OLE items, in rich edit views
- rich edit controls, using
- rich edit controls, OLE items
ms.assetid: 6c0b4efe-0fb8-4621-b5e1-fdcb8ec48c3b
caps.latest.revision: 24
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: b29c7c3b80d24ef9ddb94e09c6b5c7bf2444bb4f
ms.lasthandoff: 02/24/2017

---
# <a name="cricheditcntritem-class"></a>CRichEditCntrItem (clase)
Con [CRichEditView](../../mfc/reference/cricheditview-class.md) y [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md), proporciona la funcionalidad del control rich Edit. dentro del contexto de la arquitectura de vista de documento de MFC.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CRichEditCntrItem : public COleClientItem  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CRichEditCntrItem::CRichEditCntrItem](#cricheditcntritem)|Construye un objeto `CRichEditCntrItem`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CRichEditCntrItem::SyncToRichEditObject](#synctoricheditobject)|Activa el elemento como otro tipo.|  
  
## <a name="remarks"></a>Comentarios  
 Un "control rich edit" es una ventana en la que el usuario puede escribir y editar texto. El texto se puede asignar caracteres y el formato de párrafo y puede incluir objetos OLE incrustados. Los controles Rich edit proporcionan una interfaz de programación para dar formato al texto. Sin embargo, una aplicación debe implementar los componentes de interfaz de usuario necesarios para realizar operaciones de formato disponibles para el usuario.  
  
 `CRichEditView`mantiene el texto y la característica de formato de texto. `CRichEditDoc`mantiene la lista de elementos de cliente OLE que están en la vista. `CRichEditCntrItem`proporciona acceso del contenedor para el elemento de cliente OLE.  
  
 Este control común de Windows (y por tanto la [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) y las clases relacionadas) está disponible sólo para los programas que se ejecutan en versiones de Windows 95 ó 98 y Windows NT 3.51 y posteriores.  
  
 Para obtener un ejemplo del uso de elementos de contenedor de edición enriquecidas en una aplicación MFC, vea el [WORDPAD](../../visual-cpp-samples.md) aplicación de ejemplo.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocItem](../../mfc/reference/cdocitem-class.md)  
  
 [COleClientItem](../../mfc/reference/coleclientitem-class.md)  
  
 `CRichEditCntrItem`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxrich.h  
  
##  <a name="cricheditcntritem"></a>CRichEditCntrItem::CRichEditCntrItem  
 Llame a esta función para crear un `CRichEditCntrItem` de objetos y agregar al documento contenedor.  
  
```  
CRichEditCntrItem(
    REOBJECT* preo = NULL,  
    CRichEditDoc* pContainer = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 *preo*  
 Puntero a un [REOBJECT](http://msdn.microsoft.com/library/windows/desktop/bb787946) estructura que describe un elemento OLE. El nuevo `CRichEditCntrItem` objeto se crea en torno a este elemento OLE. Si *preo* es **NULL**, el elemento de cliente está vacío.  
  
 `pContainer`  
 Puntero al documento contenedor que contendrá este elemento. Si `pContainer` es **NULL**, debe llamar explícitamente a [COleDocument::AddItem](../../mfc/reference/coledocument-class.md#additem) para agregar este elemento de cliente a un documento.  
  
### <a name="remarks"></a>Comentarios  
 Esta función no realiza ninguna inicialización de OLE.  
  
 Para obtener más información, consulte el [REOBJECT](http://msdn.microsoft.com/library/windows/desktop/bb787946) estructura en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="synctoricheditobject"></a>CRichEditCntrItem::SyncToRichEditObject  
 Llame a esta función para sincronizar el aspecto del dispositivo, [DVASPECT](http://msdn.microsoft.com/library/windows/desktop/ms690318), de este **CRichEditCntrltem** al especificado por *reo*.  
  
```  
void SyncToRichEditObject(REOBJECT& reo);
```  
  
### <a name="parameters"></a>Parámetros  
 *REO*  
 Hacer referencia a un [REOBJECT](http://msdn.microsoft.com/library/windows/desktop/bb787946) estructura que describe un elemento OLE.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [DVASPECT](http://msdn.microsoft.com/library/windows/desktop/ms690318) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo de MFC WORDPAD](../../visual-cpp-samples.md)   
 [Clase de COleClientItem](../../mfc/reference/coleclientitem-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [CRichEditDoc (clase)](../../mfc/reference/cricheditdoc-class.md)   
 [CRichEditView (clase)](../../mfc/reference/cricheditview-class.md)

