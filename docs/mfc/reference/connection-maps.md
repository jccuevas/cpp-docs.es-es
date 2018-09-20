---
title: Mapas de conexiones | Microsoft Docs
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
ms.openlocfilehash: 1af235a597b70ac736ccd11de429d99e184d37b6
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46399644"
---
# <a name="connection-maps"></a>Mapas de conexiones

Controles OLE pueden exponer interfaces para otras aplicaciones. Estas interfaces sólo permiten el acceso desde un contenedor en el control. Si un control OLE que desea tener acceso a interfaces externas de otros objetos OLE, se debe establecer un punto de conexión. Este punto de conexión permite un control de acceso a los mapas de envío externos, como mapas de eventos o las funciones de notificación saliente.

La biblioteca Microsoft Foundation Class ofrece un modelo de programación que admite puntos de conexión. En este modelo, "conexión asigna" se utilizan para designar las interfaces o puntos de conexión para el control OLE. Mapas de conexiones contienen una macro para cada punto de conexión. Para obtener más información sobre los mapas de conexiones, vea el [CConnectionPoint](../../mfc/reference/cconnectionpoint-class.md) clase.

Normalmente, un control será compatible con solo dos puntos de conexión: uno para los eventos y otro para las notificaciones de la propiedad. Estos elementos se implementan mediante la `COleControl` clase base y requerir ningún trabajo adicional por el sistema de escritura del control. Los puntos de conexión adicionales que desea implementar en la clase deben agregarse manualmente. Para admitir mapas de conexiones y los puntos, MFC proporciona las siguientes macros:

### <a name="connection-map-declaration-and-demarcation"></a>Delimitación y declaración de mapa de conexión

|||
|-|-|
|[MACROS BEGIN_CONNECTION_PART](#begin_connection_part)|Declara una clase incrustada que implementa un punto de conexión adicionales (debe usarse en la declaración de clase).|
|[END_CONNECTION_PART](#end_connection_part)|Finaliza la declaración de un punto de conexión (debe usarse en la declaración de clase).|
|[CONNECTION_IID](#connection_iid)|Especifica el identificador de interfaz de punto de conexión del control.|
|[DECLARE_CONNECTION_MAP](#declare_connection_map)|Declara que se utilizará un mapa de conexión en una clase (debe usarse en la declaración de clase).|
|[BEGIN_CONNECTION_MAP](#begin_connection_map)|Inicia la definición de un mapa de conexión (debe usarse en la implementación de la clase).|
|[END_CONNECTION_MAP](#end_connection_map)|Termina la definición de un mapa de conexión (debe usarse en la implementación de la clase).|
|[CONNECTION_PART](#connection_part)|Especifica un punto de conexión en el mapa de conexión del control.|

Las siguientes funciones de ayudar a un receptor de establecer y desconectar una conexión mediante puntos de conexión:

### <a name="initializationtermination-of-connection-points"></a>Inicialización y terminación de puntos de conexión

|||
|-|-|
|[AfxConnectionAdvise](#afxconnectionadvise)|Establece una conexión entre un origen y receptor.|
|[AfxConnectionUnadvise](#afxconnectionunadvise)|Interrumpe una conexión entre un origen y un receptor.|

##  <a name="begin_connection_part"></a>  MACROS BEGIN_CONNECTION_PART

Utilice el BEGIN_CONNECTION_PART (macro) para empezar a la definición de puntos de conexión adicionales más allá de los puntos de conexión de notificación de evento y la propiedad.

```
BEGIN_CONNECTION_PART(theClass, localClass)
```

### <a name="parameters"></a>Parámetros

*theClass*<br/>
Especifica el nombre de la clase del control cuya conexión apunte esto.

*localClass*<br/>
Especifica el nombre de la clase local que implementa el punto de conexión.

### <a name="remarks"></a>Comentarios

En el archivo de declaración (. h) que define las funciones de miembro para la clase, iniciar el punto de conexión con el BEGIN_CONNECTION_PART (macro), a continuación, agregue el CONNECTION_IID (macro) y otras funciones de miembro que desea implementar y completar la conexión punto de mapa con el END_CONNECTION_PART (macro).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdisp.h

##  <a name="end_connection_part"></a>  END_CONNECTION_PART

Finaliza la declaración de su punto de conexión.

```
END_CONNECTION_PART(localClass)
```

### <a name="parameters"></a>Parámetros

*localClass*<br/>
Especifica el nombre de la clase local que implementa el punto de conexión.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdisp.h

##  <a name="connection_iid"></a>  CONNECTION_IID

Utilice entre las macros BEGIN_CONNECTION_PART y END_CONNECTION_PART macros para definir un identificador de interfaz para un punto de conexión compatible con el control OLE.

```
CONNECTION_IID(iid)
```

### <a name="parameters"></a>Parámetros

*IID*<br/>
El identificador de interfaz de la interfaz denominada por el punto de conexión.

### <a name="remarks"></a>Comentarios

El *iid* argumento es una interfaz identificador usado para identificar la interfaz que llamará el punto de conexión en sus receptores conectados. Por ejemplo:

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

Si el control admite puntos adicionales, use el declare_connection_map (macro) al final de la declaración de clase. A continuación, en el archivo .cpp que define las funciones miembro de la clase, utilice el BEGIN_CONNECTION_MAP (macro), CONNECTION_PART macros para cada uno de los puntos de conexión del control y la END_CONNECTION_MAP (macro) para declarar el final de la asignación de la conexión.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdisp.h

##  <a name="begin_connection_map"></a>  BEGIN_CONNECTION_MAP

Cada `COleControl`-clase derivada en el programa puede proporcionar un mapa de conexión para especificar los puntos de conexión que admitirá el control.

```
BEGIN_CONNECTION_MAP(theClass, theBase)
```

### <a name="parameters"></a>Parámetros

*theClass*<br/>
Especifica el nombre de la clase control cuya conexión asignarlo.

*theBase*<br/>
Especifica el nombre de la clase base de *theClass*.

### <a name="remarks"></a>Comentarios

En la implementación (. Funciones del archivo CPP) que define el miembro para la clase, iniciar la asignación de la conexión con el BEGIN_CONNECTION_MAP (macro) y luego agregue entradas de macro para cada uno de los puntos de conexión mediante el [CONNECTION_PART](#connection_part) macro. Por último, complete el mapa de la conexión con el [END_CONNECTION_MAP](#end_connection_map) macro.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdisp.h

##  <a name="end_connection_map"></a>  END_CONNECTION_MAP

Termina la definición de la asignación de la conexión.

```
END_CONNECTION_MAP()
```

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdisp.h

##  <a name="connection_part"></a>  CONNECTION_PART

Un punto de conexión para el control OLE se asigna a un identificador de interfaz específica.

```
CONNECTION_PART(theClass, iid, localClass)
```

### <a name="parameters"></a>Parámetros

*theClass*<br/>
Especifica el nombre de la clase del control cuya conexión apunte esto.

*IID*<br/>
El identificador de interfaz de la interfaz denominada por el punto de conexión.

*localClass*<br/>
Especifica el nombre de la clase local que implementa el punto de conexión.

### <a name="remarks"></a>Comentarios

Por ejemplo:

[!code-cpp[NVC_MFCConnectionPoints#2](../../mfc/codesnippet/cpp/connection-maps_2.cpp)]

implementa un mapa de la conexión con un punto de conexión, que llama a la `IID_ISinkInterface` interfaz.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdisp.h

##  <a name="afxconnectionadvise"></a>  AfxConnectionAdvise

Llame a esta función para establecer una conexión entre un origen, especificado por *pUnkSrc*y un receptor, especificado por *pUnkSink*.

```
BOOL AFXAPI AfxConnectionAdvise(
    LPUNKNOWN pUnkSrc,
    REFIID iid,
    LPUNKNOWN pUnkSink,
    BOOL bRefCount,
    DWORD FAR* pdwCookie);
```

### <a name="parameters"></a>Parámetros

*pUnkSrc*<br/>
Un puntero al objeto que llama a la interfaz.

*pUnkSink*<br/>
Un puntero al objeto que implementa la interfaz.

*IID*<br/>
El identificador de interfaz de la conexión.

*bRefCount*<br/>
TRUE indica que al crear la conexión debe producir el recuento de referencias de *pUnkSink* va a incrementar. FALSE indica que no se debe incrementar el recuento de referencias.

*pdwCookie*<br/>
Un puntero a un valor DWORD que se devuelve un identificador de conexión. Este valor se debe pasar como el *dwCookie* parámetro `AfxConnectionUnadvise` al desconectar la conexión.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se estableció una conexión; en caso contrario, es 0.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCConnectionPoints#8](../../mfc/codesnippet/cpp/connection-maps_3.cpp)]

### <a name="requirements"></a>Requisitos

**Encabezado:** afxctl.h

##  <a name="afxconnectionunadvise"></a>  AfxConnectionUnadvise

Llame a esta función para desconectar una conexión entre un origen, especificado por *pUnkSrc*y un receptor, especificado por *pUnkSink*.

```
BOOL AFXAPI AfxConnectionUnadvise(
    LPUNKNOWN pUnkSrc,
    REFIID iid,
    LPUNKNOWN pUnkSink,
    BOOL bRefCount,
    DWORD dwCookie);
```

### <a name="parameters"></a>Parámetros

*pUnkSrc*<br/>
Un puntero al objeto que llama a la interfaz.

*pUnkSink*<br/>
Un puntero al objeto que implementa la interfaz.

*IID*<br/>
El identificador de interfaz de la interfaz de punto de conexión.

*bRefCount*<br/>
TRUE indica que la desconexión de la conexión debe producir el recuento de referencias de *pUnkSink* va a reducir. FALSE indica que el recuento de referencias no se debería reducir.

*dwCookie*<br/>
El identificador de conexión devuelto por `AfxConnectionAdvise`.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se desconectó una conexión; en caso contrario, es 0.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCConnectionPoints#9](../../mfc/codesnippet/cpp/connection-maps_4.cpp)]

### <a name="requirements"></a>Requisitos

**Encabezado:** afxctl.h

## <a name="see-also"></a>Vea también

[Macros y funciones globales](../../mfc/reference/mfc-macros-and-globals.md)
