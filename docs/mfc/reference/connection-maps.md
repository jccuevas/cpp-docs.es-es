---
title: Mapas de conexiones | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros.maps
dev_langs:
- C++
helpviewer_keywords:
- connection maps
ms.assetid: 1f25a9bc-6d09-4614-99cf-dc38e8ddfa73
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 475314edba2a11535349991db644a4915e352ae7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33372843"
---
# <a name="connection-maps"></a>Mapas de conexiones
Controles OLE son capaces de exponer interfaces a otras aplicaciones. Estas interfaces sólo permiten el acceso de un contenedor en ese control. Si un control OLE que desea tener acceso a interfaces externas de otros objetos OLE, se debe establecer un punto de conexión. Este punto de conexión permite un control de acceso a mapas de envío externos, como mapas de eventos o funciones de notificación saliente.  
  
 La biblioteca Microsoft Foundation Class ofrece un modelo de programación que admita puntos de conexión. En este modelo, "conexión asigna" se usa para designar interfaces o puntos de conexión para el control OLE. Mapas de conexiones contienen una macro para cada punto de conexión. Para obtener más información sobre los mapas de conexiones, consulte la [CConnectionPoint](../../mfc/reference/cconnectionpoint-class.md) clase.  
  
 Normalmente, un control admite solo dos puntos de conexión: uno para eventos y otro para las notificaciones de la propiedad. Estos elementos se implementan mediante la `COleControl` clase base y no requerir ningún trabajo adicional en el escritor del control. Los puntos de conexión adicionales que desea implementar en la clase deben agregarse manualmente. Para admitir los mapas de conexiones y los puntos, MFC proporciona las macros siguientes:  
  
### <a name="connection-map-declaration-and-demarcation"></a>Demarcación y declaración de mapa de conexión  
  
|||  
|-|-|  
|[BEGIN_CONNECTION_PART](#begin_connection_part)|Declara una clase incrustada que implementa un punto de conexión adicionales (deben usarse en la declaración de clase).|  
|[END_CONNECTION_PART](#end_connection_part)|Finaliza la declaración de un punto de conexión (se debe utilizar en la declaración de clase).|  
|[CONNECTION_IID](#connection_iid)|Especifica el identificador de interfaz del control punto de conexión.|  
|[DECLARE_CONNECTION_MAP](#declare_connection_map)|Declara que se utilizará un mapa de conexión en una clase (debe usarse en la declaración de clase).|  
|[BEGIN_CONNECTION_MAP](#begin_connection_map)|Comienza la definición de un mapa de conexión (se debe usar en la implementación de la clase).|  
|[END_CONNECTION_MAP](#end_connection_map)|Termina la definición de un mapa de conexión (se debe usar en la implementación de la clase).|  
|[CONNECTION_PART](#connection_part)|Especifica un punto de conexión en el mapa de conexión del control.|  
  
 Las siguientes funciones de ayudar a un receptor de establecimiento y la desconexión de una conexión con puntos de conexión:  
  
### <a name="initializationtermination-of-connection-points"></a>Inicialización y terminación de puntos de conexión  
  
|||  
|-|-|  
|[AfxConnectionAdvise](#afxconnectionadvise)|Establece una conexión entre un origen y un receptor.|  
|[AfxConnectionUnadvise](#afxconnectionunadvise)|Interrumpe una conexión entre un origen y un receptor.|  
  
##  <a name="begin_connection_part"></a>  BEGIN_CONNECTION_PART  
 Use la `BEGIN_CONNECTION_PART` macro para comenzar la definición de puntos de conexión adicionales más allá de los puntos de conexión de notificación de evento y una propiedad.  
  
```   
BEGIN_CONNECTION_PART(theClass, localClass)   
```  
  
### <a name="parameters"></a>Parámetros  
 `theClass`  
 Especifica el nombre de la clase de control cuya conexión apunte esto es.  
  
 *localClass*  
 Especifica el nombre de la clase local que implementa el punto de conexión.  
  
### <a name="remarks"></a>Comentarios  
 En el archivo de declaración (. h) que define las funciones de miembro para la clase, iniciar el punto de conexión con el `BEGIN_CONNECTION_PART` (macro), a continuación, agregue el `CONNECTION_IID` macro y otras funciones de miembro que se va a implementar y completar la asignación de punto de conexión con el `END_CONNECTION_PART` macro.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdisp.h  
  
##  <a name="end_connection_part"></a>  END_CONNECTION_PART  
 Finaliza la declaración de su punto de conexión.  
  
```   
END_CONNECTION_PART(localClass)   
```  
  
### <a name="parameters"></a>Parámetros  
 *localClass*  
 Especifica el nombre de la clase local que implementa el punto de conexión.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdisp.h  
  
##  <a name="connection_iid"></a>  CONNECTION_IID  
 Utilice entre el `BEGIN_CONNECTION_PART` y `END_CONNECTION_PART` macros para definir un identificador de interfaz para un punto de conexión admitido por el control OLE.  
  
```   
CONNECTION_IID(iid)   
```  
  
### <a name="parameters"></a>Parámetros  
 `iid`  
 El identificador de interfaz de la interfaz denominada por el punto de conexión.  
  
### <a name="remarks"></a>Comentarios  
 El `iid` argumento es una interfaz identificador usado para identificar la interfaz que llamará el punto de conexión en sus receptores conectados. Por ejemplo:  
  
 [!code-cpp[NVC_MFCConnectionPoints#10](../../mfc/codesnippet/cpp/connection-maps_1.h)]  
  
 Especifica un punto de conexión que llama el `ISinkInterface` interfaz.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdisp.h  
  
##  <a name="declare_connection_map"></a>  DECLARE_CONNECTION_MAP  
 Cada `COleControl`-clase derivada en el programa puede proporcionar un mapa de conexión para especificar los puntos de conexión adicionales que admite el control.  
  
```   
DECLARE_CONNECTION_MAP() 
```  
  
### <a name="remarks"></a>Comentarios  
 Si el control admite puntos adicionales, use la `DECLARE_CONNECTION_MAP` macro al final de la declaración de clase. A continuación, en el archivo .cpp que define las funciones de miembro para la clase, use la `BEGIN_CONNECTION_MAP` macro, `CONNECTION_PART` macros para cada uno de los puntos de conexión del control y el `END_CONNECTION_MAP` macro para declarar el final de la asignación de conexión.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdisp.h  
  
##  <a name="begin_connection_map"></a>  BEGIN_CONNECTION_MAP  
 Cada `COleControl`-clase derivada en el programa puede proporcionar un mapa de conexión para especificar los puntos de conexión admitidas por el control.  
  
```   
BEGIN_CONNECTION_MAP(theClass, theBase)   
```  
  
### <a name="parameters"></a>Parámetros  
 `theClass`  
 Especifica el nombre de la clase de control cuya conexión asignar todo esto es.  
  
 *theBase*  
 Especifica el nombre de la clase base de `theClass`.  
  
### <a name="remarks"></a>Comentarios  
 En la implementación (. Archivo CPP) que define las funciones de miembro para la clase, se inicia el mapa de conexión con el `BEGIN_CONNECTION_MAP` macro y, a continuación, agregue entradas de macro para cada uno de los puntos de conexión con el [CONNECTION_PART](#connection_part) macro. Por último, finalice el mapa de conexión con el [END_CONNECTION_MAP](#end_connection_map) macro.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdisp.h  
  
##  <a name="end_connection_map"></a>  END_CONNECTION_MAP  
 Termina la definición de la asignación de conexión.  
  
```   
END_CONNECTION_MAP()  
```  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdisp.h  
  
##  <a name="connection_part"></a>  CONNECTION_PART  
 Un punto de conexión para el control OLE se asigna a un identificador de interfaz específico.  
  
```   
CONNECTION_PART(theClass, iid, localClass)   
```  
  
### <a name="parameters"></a>Parámetros  
 `theClass`  
 Especifica el nombre de la clase de control cuya conexión apunte esto es.  
  
 `iid`  
 El identificador de interfaz de la interfaz denominada por el punto de conexión.  
  
 *localClass*  
 Especifica el nombre de la clase local que implementa el punto de conexión.  
  
### <a name="remarks"></a>Comentarios  
 Por ejemplo:  
  
 [!code-cpp[NVC_MFCConnectionPoints#2](../../mfc/codesnippet/cpp/connection-maps_2.cpp)]  
  
 implementa un mapa de conexión, con un punto de conexión, que llama el `IID_ISinkInterface` interfaz.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdisp.h  
  
##  <a name="afxconnectionadvise"></a>  AfxConnectionAdvise  
 Llame a esta función para establecer una conexión entre un origen, especificado por `pUnkSrc`y un receptor, especificado por `pUnkSink`.  
  
```   
BOOL AFXAPI AfxConnectionAdvise(
    LPUNKNOWN pUnkSrc, 
    REFIID iid, 
    LPUNKNOWN pUnkSink, 
    BOOL bRefCount, 
    DWORD FAR* pdwCookie);
```  
  
### <a name="parameters"></a>Parámetros  
 `pUnkSrc`  
 Un puntero al objeto que llama a la interfaz.  
  
 `pUnkSink`  
 Un puntero al objeto que implementa la interfaz.  
  
 `iid`  
 El identificador de interfaz de la conexión.  
  
 `bRefCount`  
 **TRUE** indica que al crear la conexión debe producir el recuento de referencias de `pUnkSink` va a incrementar. **FALSE** indica que no se debería incrementar el recuento de referencias.  
  
 `pdwCookie`  
 Un puntero a un `DWORD` donde se devuelve un identificador de conexión. Este valor se debe pasar como el `dwCookie` parámetro `AfxConnectionUnadvise` al desconectar la conexión.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se estableció una conexión; en caso contrario es 0.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCConnectionPoints#8](../../mfc/codesnippet/cpp/connection-maps_3.cpp)]  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxctl.h 

##  <a name="afxconnectionunadvise"></a>  AfxConnectionUnadvise  
 Llame a esta función para desconectar una conexión entre un origen, especificado por `pUnkSrc`y un receptor, especificado por `pUnkSink`.  
  
```   
BOOL AFXAPI AfxConnectionUnadvise(
    LPUNKNOWN pUnkSrc, 
    REFIID iid, 
    LPUNKNOWN pUnkSink, 
    BOOL bRefCount, 
    DWORD dwCookie); 
```  
  
### <a name="parameters"></a>Parámetros  
 `pUnkSrc`  
 Un puntero al objeto que llama a la interfaz.  
  
 `pUnkSink`  
 Un puntero al objeto que implementa la interfaz.  
  
 `iid`  
 El identificador de interfaz de la interfaz de punto de conexión.  
  
 `bRefCount`  
 **TRUE** indica que la desconexión de la conexión debe hacer el recuento de referencias de `pUnkSink` sea reducido. **FALSE** indica que el recuento de referencias no debe ser reducido.  
  
 `dwCookie`  
 El identificador de conexión devuelto por `AfxConnectionAdvise`.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se desconecta una conexión; en caso contrario es 0.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCConnectionPoints#9](../../mfc/codesnippet/cpp/connection-maps_4.cpp)]  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxctl.h 

## <a name="see-also"></a>Vea también  
 [Macros y funciones globales](../../mfc/reference/mfc-macros-and-globals.md)
