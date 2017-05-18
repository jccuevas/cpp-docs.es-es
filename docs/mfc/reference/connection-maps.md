---
title: Mapas de conexiones | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.macros.maps
dev_langs:
- C++
helpviewer_keywords:
- connection maps
ms.assetid: 1f25a9bc-6d09-4614-99cf-dc38e8ddfa73
caps.latest.revision: 12
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
ms.sourcegitcommit: 17a158366f94d27b7a46917282425d652e6b9042
ms.openlocfilehash: 8947930d20cc65075abe442b233e4c086f10f76e
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="connection-maps"></a>Mapas de conexiones
Controles OLE son capaces de exponer interfaces a otras aplicaciones. Estas interfaces sólo permiten el acceso de un contenedor en el control. Si un control OLE que desea tener acceso a las interfaces externas de otros objetos OLE, se debe establecer un punto de conexión. Este punto de conexión permite un control de acceso a mapas de envío externos, como mapas de eventos o funciones de notificación saliente.  
  
 Microsoft Foundation Class Library ofrece un modelo de programación que admita puntos de conexión. En este modelo, "conexión asigna" se utilizan para designar las interfaces o puntos de conexión para el control OLE. Mapas de conexiones contienen una macro para cada punto de conexión. Para obtener más información sobre mapas de conexiones, consulte la [CConnectionPoint](../../mfc/reference/cconnectionpoint-class.md) clase.  
  
 Normalmente, un control admite solo dos puntos de conexión: uno para eventos y otro para las notificaciones de la propiedad. Éstos se implementan en la `COleControl` clase base y no requerir ningún trabajo adicional por el sistema de escritura del control. Los puntos de conexión adicionales que desee implementar en la clase deben agregarse manualmente. Para admitir los mapas de conexiones y los puntos, MFC proporciona las siguientes macros:  
  
### <a name="connection-map-declaration-and-demarcation"></a>Delimitación y declaración de mapa de conexión  
  
|||  
|-|-|  
|[BEGIN_CONNECTION_PART](#begin_connection_part)|Declara una clase incrustada que implementa un punto de conexión adicionales (se debe utilizar en la declaración de clase).|  
|[END_CONNECTION_PART](#end_connection_part)|Finaliza la declaración de un punto de conexión (se debe utilizar en la declaración de clase).|  
|[CONNECTION_IID](#connection_iid)|Especifica el identificador de interfaz del control punto de conexión.|  
|[DECLARE_CONNECTION_MAP](#declare_connection_map)|Declara que se utilizará un mapa de conexión en una clase (usada en la declaración de clase).|  
|[BEGIN_CONNECTION_MAP](#begin_connection_map)|Inicia la definición de un mapa de conexión (se debe usar en la implementación de la clase).|  
|[END_CONNECTION_MAP](#end_connection_map)|Termina la definición de un mapa de conexión (se debe usar en la implementación de la clase).|  
|[CONNECTION_PART](#connection_part)|Especifica un punto de conexión en el mapa de conexión del control.|  
  
 Las siguientes funciones de ayudar a un receptor de establecimiento y la desconexión de una conexión con puntos de conexión:  
  
### <a name="initializationtermination-of-connection-points"></a>Inicialización y terminación de puntos de conexión  
  
|||  
|-|-|  
|[AfxConnectionAdvise](#afxconnectionadvise)|Establece una conexión entre un origen y un receptor.|  
|[AfxConnectionUnadvise](#afxconnectionunadvise)|Interrumpe una conexión entre un origen y un receptor.|  
  
##  <a name="begin_connection_part"></a>BEGIN_CONNECTION_PART  
 Utilice la `BEGIN_CONNECTION_PART` macro para comenzar la definición de puntos de conexión adicionales más allá de los puntos de conexión de notificación de evento y una propiedad.  
  
```   
BEGIN_CONNECTION_PART(theClass, localClass)   
```  
  
### <a name="parameters"></a>Parámetros  
 `theClass`  
 Especifica el nombre de la clase control cuya conexión de este punto.  
  
 *localClass*  
 Especifica el nombre de la clase local que implementa el punto de conexión.  
  
### <a name="remarks"></a>Comentarios  
 En el archivo de declaración (. h) que define las funciones de miembro para la clase, iniciar el punto de conexión con el `BEGIN_CONNECTION_PART` (macro), a continuación, agregue el `CONNECTION_IID` macro y otras funciones de miembro que desea implementar y completar el mapa de puntos de conexión con el `END_CONNECTION_PART` (macro).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdisp.h  
  
##  <a name="end_connection_part"></a>END_CONNECTION_PART  
 Finaliza la declaración de su punto de conexión.  
  
```   
END_CONNECTION_PART(localClass)   
```  
  
### <a name="parameters"></a>Parámetros  
 *localClass*  
 Especifica el nombre de la clase local que implementa el punto de conexión.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdisp.h  
  
##  <a name="connection_iid"></a>CONNECTION_IID  
 Utilice entre el `BEGIN_CONNECTION_PART` y `END_CONNECTION_PART` macros para definir un identificador de interfaz para un punto de conexión admitido por el control OLE.  
  
```   
CONNECTION_IID(iid)   
```  
  
### <a name="parameters"></a>Parámetros  
 `iid`  
 El identificador de la interfaz de la interfaz denominada por el punto de conexión.  
  
### <a name="remarks"></a>Comentarios  
 El `iid` argumento es una interfaz identificador usado para identificar la interfaz que llamará el punto de conexión en sus receptores conectados. Por ejemplo:  
  
 [!code-cpp[NVC_MFCConnectionPoints&#10;](../../mfc/codesnippet/cpp/connection-maps_1.h)]  
  
 Especifica un punto de conexión que llama el `ISinkInterface` interfaz.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdisp.h  
  
##  <a name="declare_connection_map"></a>DECLARE_CONNECTION_MAP  
 Cada `COleControl`-clase derivada en el programa puede proporcionar un mapa de conexión para especificar los puntos de conexión adicionales que admite el control.  
  
```   
DECLARE_CONNECTION_MAP() 
```  
  
### <a name="remarks"></a>Comentarios  
 Si el control admite puntos adicionales, use la `DECLARE_CONNECTION_MAP` macro al final de la declaración de clase. A continuación, en el archivo .cpp que define las funciones de miembro para la clase, use la `BEGIN_CONNECTION_MAP` (macro), `CONNECTION_PART` macros para cada uno de los puntos de conexión del control y el `END_CONNECTION_MAP` macro para declarar el final de la asignación de la conexión.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdisp.h  
  
##  <a name="begin_connection_map"></a>BEGIN_CONNECTION_MAP  
 Cada `COleControl`-clase derivada en el programa puede proporcionar un mapa de conexión para especificar los puntos de conexión compatibles con el control.  
  
```   
BEGIN_CONNECTION_MAP(theClass, theBase)   
```  
  
### <a name="parameters"></a>Parámetros  
 `theClass`  
 Especifica el nombre de la clase control cuya conexión asignar todo esto.  
  
 *theBase*  
 Especifica el nombre de la clase base de `theClass`.  
  
### <a name="remarks"></a>Comentarios  
 En la implementación (. Archivo CPP) que define las funciones de miembro para la clase, iniciar el mapa de conexión con el `BEGIN_CONNECTION_MAP` (macro), a continuación, agregue entradas de macro para cada uno de los puntos de conexión con el [CONNECTION_PART](#connection_part) (macro). Por último, complete el mapa de conexión con el [END_CONNECTION_MAP](#end_connection_map) (macro).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdisp.h  
  
##  <a name="end_connection_map"></a>END_CONNECTION_MAP  
 Termina la definición de la asignación de la conexión.  
  
```   
END_CONNECTION_MAP()  
```  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdisp.h  
  
##  <a name="connection_part"></a>CONNECTION_PART  
 Un punto de conexión para el control OLE se asigna a un identificador de interfaz concreto.  
  
```   
CONNECTION_PART(theClass, iid, localClass)   
```  
  
### <a name="parameters"></a>Parámetros  
 `theClass`  
 Especifica el nombre de la clase control cuya conexión de este punto.  
  
 `iid`  
 El identificador de la interfaz de la interfaz denominada por el punto de conexión.  
  
 *localClass*  
 Especifica el nombre de la clase local que implementa el punto de conexión.  
  
### <a name="remarks"></a>Comentarios  
 Por ejemplo:  
  
 [!code-cpp[NVC_MFCConnectionPoints&#2;](../../mfc/codesnippet/cpp/connection-maps_2.cpp)]  
  
 implementa un mapa de conexión con un punto de conexión que llama el `IID_ISinkInterface` interfaz.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdisp.h  
  
##  <a name="afxconnectionadvise"></a>AfxConnectionAdvise  
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
 El identificador de la interfaz de la conexión.  
  
 `bRefCount`  
 **TRUE** indica que al crear la conexión debe hacer el recuento de referencias de `pUnkSink` va a incrementar. **FALSE** indica que no se debería incrementar el recuento de referencias.  
  
 `pdwCookie`  
 Un puntero a un `DWORD` donde se devuelve un identificador de conexión. Este valor se debe pasar como el `dwCookie` parámetro `AfxConnectionUnadvise` al desconectar la conexión.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si se estableció una conexión; en caso contrario, 0.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCConnectionPoints Nº&8;](../../mfc/codesnippet/cpp/connection-maps_3.cpp)]  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxctl.h 

##  <a name="afxconnectionunadvise"></a>AfxConnectionUnadvise  
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
 El identificador de la interfaz de la interfaz de punto de conexión.  
  
 `bRefCount`  
 **TRUE** indica que la desconexión de la conexión debe hacer el recuento de referencias de `pUnkSink` va a reducir. **FALSE** indica que el recuento de referencias no se debería reducir.  
  
 `dwCookie`  
 Devuelve el identificador de conexión `AfxConnectionAdvise`.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si se desconecta una conexión; en caso contrario, 0.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCConnectionPoints&#9;](../../mfc/codesnippet/cpp/connection-maps_4.cpp)]  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxctl.h 

## <a name="see-also"></a>Vea también  
 [Macros y funciones globales](../../mfc/reference/mfc-macros-and-globals.md)

