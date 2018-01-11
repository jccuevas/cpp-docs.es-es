---
title: Clase CDocObjectServer | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDocObjectServer
- AFXDOCOB/CDocObjectServer
- AFXDOCOB/CDocObjectServer::CDocObjectServer
- AFXDOCOB/CDocObjectServer::ActivateDocObject
- AFXDOCOB/CDocObjectServer::OnActivateView
- AFXDOCOB/CDocObjectServer::OnApplyViewState
- AFXDOCOB/CDocObjectServer::OnSaveViewState
dev_langs: C++
helpviewer_keywords:
- CDocObjectServer [MFC], CDocObjectServer
- CDocObjectServer [MFC], ActivateDocObject
- CDocObjectServer [MFC], OnActivateView
- CDocObjectServer [MFC], OnApplyViewState
- CDocObjectServer [MFC], OnSaveViewState
ms.assetid: 18cd0dff-0616-4472-b8d9-66c081bc383a
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 912262c4f1ba85c181bb30ee5d6f38a0defe5d5d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cdocobjectserver-class"></a>Clase CDocObjectServer
Implementa las interfaces OLE adicionales necesarias para crear un servidor normal de `COleDocument` en un servidor completo de DocObject: `IOleDocument`, `IOleDocumentView`, `IOleCommandTarget`y `IPrint`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CDocObjectServer : public CCmdTarget  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDocObjectServer::CDocObjectServer](#cdocobjectserver)|Construye un objeto `CDocObjectServer`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDocObjectServer::ActivateDocObject](#activatedocobject)|Activa el servidor de objetos de documento, pero no se muestra.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDocObjectServer::OnActivateView](#onactivateview)|Muestra la vista de DocObject.|  
|[CDocObjectServer::OnApplyViewState](#onapplyviewstate)|Restaura el estado de la vista de DocObject.|  
|[CDocObjectServer::OnSaveViewState](#onsaveviewstate)|Guarda el estado de la vista de DocObject.|  
  
## <a name="remarks"></a>Comentarios  
 `CDocObjectServer`se deriva de `CCmdTarget` y trabaja en estrecha colaboración con `COleServerDoc` para exponer las interfaces.  
  
 Puede contener un documento de servidor DocObject [CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md) objetos que representan la interfaz de servidor a los elementos de DocObject.  
  
 Para personalizar el servidor de DocObject, derive su propia clase de `CDocObjectServer` y reemplazar sus funciones de configuración de vista, [OnActivateView](#onactivateview), [OnApplyViewState](#onapplyviewstate), y [OnSaveViewState ](#onsaveviewstate). Debe proporcionar una nueva instancia de la clase en respuesta a las llamadas de framework.  
  
 Para obtener más información sobre DocObjects, consulte [CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md) y [COleCmdUI](../../mfc/reference/colecmdui-class.md) en el *referencia de MFC*. Consulte también [primeros pasos de Internet: documentos activos](../../mfc/active-documents-on-the-internet.md) y [documentos activos](../../mfc/active-documents-on-the-internet.md).  
  
 Consulte también el artículo de Knowledge Base siguiente:  
  
-   Q247382: PRB: información sobre herramientas para controles de servidor de documentos ActiveX está ocultos por el contenedor de documentos de ActiveX  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CDocObjectServer`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdocob.h  
  
##  <a name="activatedocobject"></a>CDocObjectServer::ActivateDocObject  
 Llame a esta función para activar el servidor de objetos de documento (pero no mostrar).  
  
```  
void ActivateDocObject();
```  
  
### <a name="remarks"></a>Comentarios  
 `ActivateDocObject`llamadas `IOleDocumentSite`del **ActivateMe** método, pero no se muestra la vista porque se espera para obtener instrucciones específicas sobre cómo configurar y mostrar la vista, se proporcionan en la llamada a [CDocObjectServer::OnActivateView](#onactivateview).  
  
 Juntos, `ActivateDocObject` y `OnActivateView` activar y mostrar la vista de DocObject. Activación de DocObject difiere de otros tipos de activación en contexto OLE. Activación de DocObject omite la presentación de los bordes de trama en contexto y opciones gráficas del objeto (por ejemplo, controladores de tamaño), pasa por alto las funciones de extensión de objeto y dibuja las barras de desplazamiento dentro del rectángulo de la vista en lugar de dibujar a ellos fuera de dicho rectángulo (como en normal activación en contexto).  
  
##  <a name="cdocobjectserver"></a>CDocObjectServer::CDocObjectServer  
 Construye e inicializa un objeto `CDocObjectServer`.  
  
```  
explicit CDocObjectServer(
    COleServerDoc* pOwner,  
    LPOLEDOCUMENTSITE pDocSite = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 *pOwner*  
 Un puntero al documento de sitio de cliente es el cliente para el servidor de DocObject.  
  
 `pDocSite`  
 Un puntero a la `IOleDocumentSite` interfaz implementada por el contenedor.  
  
### <a name="remarks"></a>Comentarios  
 Cuando un DocObject está activo, el cliente del sitio OLE (interfaz) ( `IOleDocumentSite`) es lo que permite al servidor de DocObject para comunicarse con su cliente (el contenedor). Cuando se activa un servidor DocObject, en primer lugar comprueba que el contenedor implementa el `IOleDocumentSite` interfaz. Si es así, [COleServerDoc::GetDocObjectServer](../../mfc/reference/coleserverdoc-class.md#getdocobjectserver) se llama para ver si el contenedor admite DocObjects. De forma predeterminada, `GetDocObjectServer` devuelve **NULL**. Debe invalidar `COleServerDoc::GetDocObjectServer` para crear un nuevo `CDocObjectServer` objeto o un objeto derivado de los suyos propios con punteros a la `COleServerDoc` contenedor y su `IOleDocumentSite` interfaz como argumentos del constructor.  
  
##  <a name="onactivateview"></a>CDocObjectServer::OnActivateView  
 Llame a esta función para mostrar la vista de DocObject.  
  
```  
virtual HRESULT OnActivateView();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un valor de advertencia o error. De forma predeterminada, devuelve **NOERROR** si es correcto; en caso contrario, **E_FAIL**.  
  
### <a name="remarks"></a>Comentarios  
 Esta función crea una ventana de marco en contexto, dibuja las barras de desplazamiento dentro de la vista, configura los menús el servidor comparte con su contenedor, agrega controles de marco, Establece el objeto activo, a continuación, por último, muestra la ventana de marco en contexto y establece el foco.  
  
##  <a name="onapplyviewstate"></a>CDocObjectServer::OnApplyViewState  
 Reemplace esta función para restaurar el estado de la vista de DocObject.  
  
```  
virtual void OnApplyViewState(CArchive& ar);
```  
  
### <a name="parameters"></a>Parámetros  
 `ar`  
 Un `CArchive` objeto desde el que se va a serializar el estado de vista.  
  
### <a name="remarks"></a>Comentarios  
 Esta función se invoca cuando se muestra la vista por primera vez después de la creación de instancias. `OnApplyViewState`indica a una vista que se reinicialice según los datos en el `CArchive` objeto guardado previamente con [OnSaveViewState](#onsaveviewstate). La vista debe validar los datos en el `CArchive` porque el contenedor no intenta interpretar los datos de estado de vista en forma de objeto.  
  
 Puede usar `OnSaveViewState` para almacenar información persistente específica al estado de la vista. Si invalida `OnSaveViewState` para almacenar la información, desea invalidar `OnApplyViewState` para leer esa información y aplicarlo a la vista cuando se activa a recientemente.  
  
##  <a name="onsaveviewstate"></a>CDocObjectServer::OnSaveViewState  
 Reemplace esta función para guardar información de estado adicionales sobre la vista de DocObject.  
  
```  
virtual void OnSaveViewState(CArchive& ar);
```  
  
### <a name="parameters"></a>Parámetros  
 `ar`  
 Un `CArchive` de objeto para el que se serializa el estado de vista.  
  
### <a name="remarks"></a>Comentarios  
 El estado puede incluir propiedades, como el tipo de vista, el factor de zoom, inserción y punto de selección y así sucesivamente. El contenedor llama normalmente a esta función antes de desactivar la vista. Más adelante se puede restaurar el estado guardado mediante [OnApplyViewState](#onapplyviewstate).  
  
 Puede usar `OnSaveViewState` para almacenar información persistente específica al estado de la vista. Si invalida `OnSaveViewState` para almacenar la información, desea invalidar `OnApplyViewState` para leer esa información y aplicarlo a la vista cuando se activa a recientemente.  
  
## <a name="see-also"></a>Vea también  
 [CCmdTarget (clase)](../../mfc/reference/ccmdtarget-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CDocObjectServerItem (clase)](../../mfc/reference/cdocobjectserveritem-class.md)
