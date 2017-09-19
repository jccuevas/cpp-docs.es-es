---
title: Clase CDocObjectServer | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
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
dev_langs:
- C++
helpviewer_keywords:
- document object server
- CDocObjectServer class
- servers [C++], ActiveX documents
- docobject server
- servers [C++], doc objects
- ActiveX documents [C++], document server
ms.assetid: 18cd0dff-0616-4472-b8d9-66c081bc383a
caps.latest.revision: 23
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 75fb0ba49d105a673e862ed3044e85ac9e990e9c
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="cdocobjectserver-class"></a>Clase CDocObjectServer
Implementa las interfaces OLE adicionales necesarias para crear un servidor normal de `COleDocument` en un servidor completo de DocObject: `IOleDocument`, `IOleDocumentView`, `IOleCommandTarget`y `IPrint`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CDocObjectServer : public CCmdTarget  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CDocObjectServer::CDocObjectServer](#cdocobjectserver)|Construye un objeto `CDocObjectServer`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CDocObjectServer::ActivateDocObject](#activatedocobject)|Activa el servidor de objetos de documento, pero no la muestra.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CDocObjectServer::OnActivateView](#onactivateview)|Muestra la vista DocObject.|  
|[CDocObjectServer::OnApplyViewState](#onapplyviewstate)|Restaura el estado de la vista DocObject.|  
|[CDocObjectServer::OnSaveViewState](#onsaveviewstate)|Guarda el estado de la vista DocObject.|  
  
## <a name="remarks"></a>Comentarios  
 `CDocObjectServer`se deriva de `CCmdTarget` y trabaja en estrecha colaboración con `COleServerDoc` para exponer las interfaces.  
  
 Puede contener un documento del servidor DocObject [CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md) objetos que representan la interfaz de servidor a elementos de DocObject.  
  
 Para personalizar el servidor DocObject, derive su propia clase de `CDocObjectServer` e invalidar sus funciones de configuración de vista, [OnActivateView](#onactivateview), [OnApplyViewState](#onapplyviewstate), y [OnSaveViewState](#onsaveviewstate). Debe proporcionar una nueva instancia de la clase en respuesta a llamadas de framework.  
  
 Para obtener más información sobre DocObjects, consulte [CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md) y [COleCmdUI](../../mfc/reference/colecmdui-class.md) en el *referencia de MFC*. Consulte también [primeros pasos de Internet: documentos activos](../../mfc/active-documents-on-the-internet.md) y [documentos activos](../../mfc/active-documents-on-the-internet.md).  
  
 Consulte también el siguiente artículo de Knowledge Base:  
  
-   Q247382: PRB: información sobre herramientas para controles de servidor de documentos ActiveX está ocultos por el contenedor de documentos ActiveX  
  
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
 `ActivateDocObject`llamadas `IOleDocumentSite`de **ActivateMe** método, pero no muestra la vista porque se espera para obtener instrucciones específicas acerca de cómo configurar y mostrar la vista en la llamada a [CDocObjectServer::OnActivateView](#onactivateview).  
  
 Juntos, `ActivateDocObject` y `OnActivateView` activar y mostrar la vista DocObject. Activación de DocObject difiere de otros tipos de activación en contexto OLE. Activación de DocObject hace que no aparezcan bordes de trama en contexto y elementos gráficos de objeto (por ejemplo, controladores de tamaño), omite las funciones de extensión de objeto y dibuja las barras de desplazamiento dentro del rectángulo de la vista en lugar de dibujar a ellos fuera del rectángulo (como en la activación en contexto normal).  
  
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
 Cuando DocObject está activa, el cliente de sitio OLE (interfaz) ( `IOleDocumentSite`) es lo que permite que el servidor DocObject para comunicarse con su cliente (el contenedor). Cuando se activa un servidor DocObject, primero comprueba que el contenedor implementa el `IOleDocumentSite` interfaz. Si es así, [COleServerDoc::GetDocObjectServer](../../mfc/reference/coleserverdoc-class.md#getdocobjectserver) se llama para ver si el contenedor admite DocObjects. De forma predeterminada, `GetDocObjectServer` devuelve **NULL**. Debe invalidar `COleServerDoc::GetDocObjectServer` para crear un nuevo `CDocObjectServer` objeto o un objeto derivado de los suyos propios con punteros a la `COleServerDoc` contenedor y su `IOleDocumentSite` interfaz como argumentos del constructor.  
  
##  <a name="onactivateview"></a>CDocObjectServer::OnActivateView  
 Llame a esta función para mostrar la vista DocObject.  
  
```  
virtual HRESULT OnActivateView();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un valor de advertencia o error. De forma predeterminada, devuelve **NOERROR** si es correcto; en caso contrario, **E_FAIL**.  
  
### <a name="remarks"></a>Comentarios  
 Esta función crea una ventana de marco en contexto, dibuja las barras de desplazamiento dentro de la vista, configura los menús el servidor comparte con su contenedor, agrega controles de marco, Establece el objeto activo, y finalmente muestra la ventana de marco en contexto y establece el foco.  
  
##  <a name="onapplyviewstate"></a>CDocObjectServer::OnApplyViewState  
 Reemplazar esta función para restaurar el estado de la vista DocObject.  
  
```  
virtual void OnApplyViewState(CArchive& ar);
```  
  
### <a name="parameters"></a>Parámetros  
 `ar`  
 Un `CArchive` objeto desde el que se va a serializar el estado de vista.  
  
### <a name="remarks"></a>Comentarios  
 Esta función se invoca cuando se muestra la vista por primera vez después de la creación de instancias. `OnApplyViewState`indica a una vista que se reinicialice según los datos de la `CArchive` objeto guardado previamente con [OnSaveViewState](#onsaveviewstate). La vista debe validar los datos en el `CArchive` porque el contenedor no intenta interpretar los datos de estado de vista en forma de objeto.  
  
 Puede usar `OnSaveViewState` para almacenar información persistente específica al estado de la vista. Si reemplaza `OnSaveViewState` para almacenar información, desea invalidar `OnApplyViewState` para leer esa información y aplicarlo a la vista cuando recién se activa.  
  
##  <a name="onsaveviewstate"></a>CDocObjectServer::OnSaveViewState  
 Reemplazar esta función para guardar información de estado adicionales sobre la vista DocObject.  
  
```  
virtual void OnSaveViewState(CArchive& ar);
```  
  
### <a name="parameters"></a>Parámetros  
 `ar`  
 Un `CArchive` de objeto para el que se serializa el estado de vista.  
  
### <a name="remarks"></a>Comentarios  
 El estado puede incluir propiedades como el tipo de vista, el factor de zoom, inserción y punto de selección y así sucesivamente. El contenedor llama normalmente a esta función antes de desactivar la vista. Más adelante se puede restaurar el estado guardado con [OnApplyViewState](#onapplyviewstate).  
  
 Puede usar `OnSaveViewState` para almacenar información persistente específica al estado de la vista. Si reemplaza `OnSaveViewState` para almacenar información, desea invalidar `OnApplyViewState` para leer esa información y aplicarlo a la vista cuando recién se activa.  
  
## <a name="see-also"></a>Vea también  
 [CCmdTarget (clase)](../../mfc/reference/ccmdtarget-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clase CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md)

