---
title: Mapas de conexiones
ms.date: 11/04/2016
helpviewer_keywords:
- connection maps
ms.assetid: 1f25a9bc-6d09-4614-99cf-dc38e8ddfa73
ms.openlocfilehash: 947cd09023ef4028a32db8e2e4e8b33f7e04e0dd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374803"
---
# <a name="connection-maps"></a>Mapas de conexiones

Los controles OLE pueden exponer interfaces a otras aplicaciones. Estas interfaces solo permiten el acceso desde un contenedor a ese control. Si un control OLE desea tener acceso a interfaces externas de otros objetos OLE, se debe establecer un punto de conexión. Este punto de conexión permite controlar el acceso saliente a mapas de envío externos, como mapas de eventos o funciones de notificación.

La biblioteca Microsoft Foundation Class ofrece un modelo de programación que admite puntos de conexión. En este modelo, se utilizan "mapas de conexión" para designar interfaces o puntos de conexión para el control OLE. Los mapas de conexión contienen una macro para cada punto de conexión. Para obtener más información sobre las asignaciones de conexión, vea la [clase CConnectionPoint.](../../mfc/reference/cconnectionpoint-class.md)

Normalmente, un control admitirá solo dos puntos de conexión: uno para eventos y otro para notificaciones de propiedad. Estos son implementados `COleControl` por la clase base y no requieren ningún trabajo adicional por el escritor de control. Los puntos de conexión adicionales que desee implementar en la clase se deben agregar manualmente. Para admitir puntos y asignaciones de conexión, MFC proporciona las siguientes macros:

### <a name="connection-map-declaration-and-demarcation"></a>Declaración y demarcación del mapa de conexión

|||
|-|-|
|[BEGIN_CONNECTION_PART](#begin_connection_part)|Declara una clase incrustada que implementa un punto de conexión adicional (debe usarse en la declaración de clase).|
|[END_CONNECTION_PART](#end_connection_part)|Finaliza la declaración de un punto de conexión (debe utilizarse en la declaración de clase).|
|[CONNECTION_IID](#connection_iid)|Especifica el identificador de interfaz del punto de conexión del control.|
|[DECLARE_CONNECTION_MAP](#declare_connection_map)|Declara que se usará una asignación de conexión en una clase (debe utilizarse en la declaración de clase).|
|[BEGIN_CONNECTION_MAP](#begin_connection_map)|Comienza la definición de un mapa de conexión (debe usarse en la implementación de la clase).|
|[END_CONNECTION_MAP](#end_connection_map)|Finaliza la definición de un mapa de conexión (debe utilizarse en la implementación de la clase).|
|[CONNECTION_PART](#connection_part)|Especifica un punto de conexión en el mapa de conexión del control.|

Las siguientes funciones ayudan a un receptor a establecer y desconectar una conexión mediante puntos de conexión:

### <a name="initializationtermination-of-connection-points"></a>Inicialización/Terminación de Puntos de Conexión

|||
|-|-|
|[AfxConnectionAdvise](#afxconnectionadvise)|Establece una conexión entre un origen y un receptor.|
|[AfxConnectionUnadvise](#afxconnectionunadvise)|Rompe una conexión entre un origen y un receptor.|

## <a name="begin_connection_part"></a><a name="begin_connection_part"></a>BEGIN_CONNECTION_PART

Utilice la macro BEGIN_CONNECTION_PART para iniciar la definición de puntos de conexión adicionales más allá de los puntos de conexión de notificación de eventos y propiedades.

```
BEGIN_CONNECTION_PART(theClass, localClass)
```

### <a name="parameters"></a>Parámetros

*theClass*<br/>
Especifica el nombre de la clase de control cuyo punto de conexión es.

*localClass*<br/>
Especifica el nombre de la clase local que implementa el punto de conexión.

### <a name="remarks"></a>Observaciones

En el archivo de declaración (.h) que define las funciones miembro de la clase, inicie el punto de conexión con la macro BEGIN_CONNECTION_PART, agregue la macro CONNECTION_IID y cualquier otra función miembro que desee implementar y complete el mapa de punto de conexión con la macro END_CONNECTION_PART.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdisp.h

## <a name="end_connection_part"></a><a name="end_connection_part"></a>END_CONNECTION_PART

Finaliza la declaración del punto de conexión.

```
END_CONNECTION_PART(localClass)
```

### <a name="parameters"></a>Parámetros

*localClass*<br/>
Especifica el nombre de la clase local que implementa el punto de conexión.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdisp.h

## <a name="connection_iid"></a><a name="connection_iid"></a>CONNECTION_IID

Use entre las macros BEGIN_CONNECTION_PART y END_CONNECTION_PART para definir un identificador de interfaz para un punto de conexión admitido por el control OLE.

```
CONNECTION_IID(iid)
```

### <a name="parameters"></a>Parámetros

*Iid*<br/>
El ID de interfaz de la interfaz a la que llama el punto de conexión.

### <a name="remarks"></a>Observaciones

El argumento *iid* es un identificador de interfaz utilizado para identificar la interfaz a la que el punto de conexión llamará en sus receptores conectados. Por ejemplo:

[!code-cpp[NVC_MFCConnectionPoints#10](../../mfc/codesnippet/cpp/connection-maps_1.h)]

especifica un punto de `ISinkInterface` conexión que llama a la interfaz.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdisp.h

## <a name="declare_connection_map"></a><a name="declare_connection_map"></a>DECLARE_CONNECTION_MAP

Cada `COleControl`clase derivada del programa puede proporcionar un mapa de conexión para especificar puntos de conexión adicionales que admita el control.

```
DECLARE_CONNECTION_MAP()
```

### <a name="remarks"></a>Observaciones

Si el control admite puntos adicionales, utilice la macro DECLARE_CONNECTION_MAP al final de la declaración de clase. A continuación, en el archivo .cpp que define las funciones miembro de la clase, use la macro BEGIN_CONNECTION_MAP, CONNECTION_PART macros para cada uno de los puntos de conexión del control y la macro END_CONNECTION_MAP para declarar el final de la asignación de conexión.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdisp.h

## <a name="begin_connection_map"></a><a name="begin_connection_map"></a>BEGIN_CONNECTION_MAP

Cada `COleControl`clase derivada del programa puede proporcionar un mapa de conexión para especificar los puntos de conexión que admitirá el control.

```
BEGIN_CONNECTION_MAP(theClass, theBase)
```

### <a name="parameters"></a>Parámetros

*theClass*<br/>
Especifica el nombre de la clase de control cuyo mapa de conexión es.

*theBase*<br/>
Especifica el nombre de la clase base de *theClass*.

### <a name="remarks"></a>Observaciones

En la implementación (. CPP) que define las funciones miembro de la clase, inicie el mapa de conexión con la macro BEGIN_CONNECTION_MAP y, a continuación, agregue entradas de macro para cada uno de los puntos de conexión mediante la macro [CONNECTION_PART.](#connection_part) Por último, complete el mapa de conexión con la macro [END_CONNECTION_MAP.](#end_connection_map)

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdisp.h

## <a name="end_connection_map"></a><a name="end_connection_map"></a>END_CONNECTION_MAP

Finaliza la definición del mapa de conexión.

```
END_CONNECTION_MAP()
```

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdisp.h

## <a name="connection_part"></a><a name="connection_part"></a>CONNECTION_PART

Asigna un punto de conexión para el control OLE a un identificador de interfaz específico.

```
CONNECTION_PART(theClass, iid, localClass)
```

### <a name="parameters"></a>Parámetros

*theClass*<br/>
Especifica el nombre de la clase de control cuyo punto de conexión es.

*Iid*<br/>
El ID de interfaz de la interfaz a la que llama el punto de conexión.

*localClass*<br/>
Especifica el nombre de la clase local que implementa el punto de conexión.

### <a name="remarks"></a>Observaciones

Por ejemplo:

[!code-cpp[NVC_MFCConnectionPoints#2](../../mfc/codesnippet/cpp/connection-maps_2.cpp)]

implementa una asignación de conexión, con `IID_ISinkInterface` un punto de conexión, que llama a la interfaz.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdisp.h

## <a name="afxconnectionadvise"></a><a name="afxconnectionadvise"></a>AfxConnectionAdvise

Llame a esta función para establecer una conexión entre un origen, especificado por *pUnkSrc*, y un receptor, especificado por *pUnkSink*.

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
Puntero al objeto que llama a la interfaz.

*pUnkSink*<br/>
Puntero al objeto que implementa la interfaz.

*Iid*<br/>
El ID de interfaz de la conexión.

*bRefCount*<br/>
TRUE indica que la creación de la conexión debe hacer que se incremente el recuento de referencias de *pUnkSink.* FALSE indica que no se debe incrementar el recuento de referencias.

*pdwCookie*<br/>
Puntero a un DWORD donde se devuelve un identificador de conexión. Este valor debe pasarse como `AfxConnectionUnadvise` parámetro *dwCookie* al desconectar la conexión.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se estableció una conexión; de lo contrario 0.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCConnectionPoints#8](../../mfc/codesnippet/cpp/connection-maps_3.cpp)]

### <a name="requirements"></a>Requisitos

**Encabezado:** afxctl.h

## <a name="afxconnectionunadvise"></a><a name="afxconnectionunadvise"></a>AfxConnectionUnadvise

Llame a esta función para desconectar una conexión entre un origen, especificado por *pUnkSrc*, y un receptor, especificado por *pUnkSink*.

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
Puntero al objeto que llama a la interfaz.

*pUnkSink*<br/>
Puntero al objeto que implementa la interfaz.

*Iid*<br/>
El ID de interfaz de la interfaz del punto de conexión.

*bRefCount*<br/>
TRUE indica que la desconexión de la conexión debe hacer que se decremente el recuento de referencias de *pUnkSink.* FALSE indica que el recuento de referencias no debe disminuirse.

*dwCookie*<br/>
Identificador de conexión `AfxConnectionAdvise`devuelto por .

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se desconectó una conexión; de lo contrario 0.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCConnectionPoints#9](../../mfc/codesnippet/cpp/connection-maps_4.cpp)]

### <a name="requirements"></a>Requisitos

**Encabezado:** afxctl.h

## <a name="see-also"></a>Consulte también

[Macros y variables globales](../../mfc/reference/mfc-macros-and-globals.md)
