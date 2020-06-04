---
title: CConnectionPoint (clase)
ms.date: 11/04/2016
f1_keywords:
- CConnectionPoint
- AFXDISP/CConnectionPoint
- AFXDISP/CConnectionPoint::CConnectionPoint
- AFXDISP/CConnectionPoint::GetConnections
- AFXDISP/CConnectionPoint::GetContainer
- AFXDISP/CConnectionPoint::GetIID
- AFXDISP/CConnectionPoint::GetMaxConnections
- AFXDISP/CConnectionPoint::GetNextConnection
- AFXDISP/CConnectionPoint::GetStartPosition
- AFXDISP/CConnectionPoint::OnAdvise
- AFXDISP/CConnectionPoint::QuerySinkInterface
helpviewer_keywords:
- CConnectionPoint [MFC], CConnectionPoint
- CConnectionPoint [MFC], GetConnections
- CConnectionPoint [MFC], GetContainer
- CConnectionPoint [MFC], GetIID
- CConnectionPoint [MFC], GetMaxConnections
- CConnectionPoint [MFC], GetNextConnection
- CConnectionPoint [MFC], GetStartPosition
- CConnectionPoint [MFC], OnAdvise
- CConnectionPoint [MFC], QuerySinkInterface
ms.assetid: f0f23a1e-5e8c-41a9-aa6c-1a4793b28e8f
ms.openlocfilehash: ce72c156ab31b742a42d2960923fc56afff656c0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369427"
---
# <a name="cconnectionpoint-class"></a>CConnectionPoint (clase)

Define un tipo especial de interfaz que se utiliza para comunicarse con otros objetos OLE, denominado "punto de conexión".

## <a name="syntax"></a>Sintaxis

```
class CConnectionPoint : public CCmdTarget
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CConnectionPoint::CConnectionPoint](#cconnectionpoint)|Construye un objeto `CConnectionPoint`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CConnectionPoint::GetConnections](#getconnections)|Recupera todos los puntos de conexión de un mapa de conexión.|
|[CConnectionPoint::GetContainer](#getcontainer)|Recupera el contenedor del control que posee el mapa de conexión.|
|[CConnectionPoint::GetIID](#getiid)|Recupera el identificador de interfaz de un punto de conexión.|
|[CConnectionPoint::GetMaxConnections](#getmaxconnections)|Recupera el número máximo de puntos de conexión admitidos por un control.|
|[CConnectionPoint::GetNextConnection](#getnextconnection)|Recupera un puntero al elemento de conexión en *pos*.|
|[CConnectionPoint::GetStartPosition](#getstartposition)|Inicia una iteración de mapa devolviendo `GetNextConnection` un valor POSITION que se puede pasar a una llamada.|
|[CConnectionPoint::OnAdvise](#onadvise)|Llamado por el marco de trabajo al establecer o interrumpir conexiones.|
|[CConnectionPoint::QuerySinkInterface](#querysinkinterface)|Recupera un puntero a la interfaz de receptor solicitada.|

## <a name="remarks"></a>Observaciones

A diferencia de las interfaces OLE normales, que se usan para implementar y exponer la funcionalidad de un control OLE, un punto de conexión implementa una interfaz saliente que puede iniciar acciones en otros objetos, como desencadenar eventos y notificaciones de cambio.

Una conexión consta de dos partes: el objeto que llama a la interfaz, denominada "fuente", y el objeto que implementa la interfaz, denominado "sink." Al exponer un punto de conexión, un origen permite que los receptores establezcan conexiones consigo mismo. A través del mecanismo de punto de conexión, un objeto de origen obtiene un puntero a la implementación del receptor de un conjunto de funciones miembro. Por ejemplo, para desencadenar un evento implementado por el receptor, el origen puede llamar al método adecuado de la implementación del receptor.

De forma `COleControl`predeterminada, una clase derivada implementa dos puntos de conexión: uno para eventos y otro para las notificaciones de cambio de propiedad. Estas conexiones se utilizan, respectivamente, para desencadenar eventos y para notificar a un receptor (por ejemplo, el contenedor del control) cuando ha cambiado un valor de propiedad. También se proporciona compatibilidad con controles OLE para implementar puntos de conexión adicionales. Para cada punto de conexión adicional implementado en la clase de control, debe declarar una "parte de conexión" que implementa el punto de conexión. Si implementa uno o varios puntos de conexión, también debe declarar un único "mapa de conexión" en la clase de control.

En el ejemplo siguiente se muestra una asignación de conexión simple y un punto de conexión para el `Sample` control OLE, que consta de dos fragmentos de código: la primera parte declara el mapa de conexión y el punto; el segundo implementa este mapa y punto. El primer fragmento se inserta en la declaración de la clase de control, en la sección **protegida:**

[!code-cpp[NVC_MFCConnectionPoints#7](../../mfc/codesnippet/cpp/cconnectionpoint-class_1.h)]

Las macros BEGIN_CONNECTION_PART y END_CONNECTION_PART declaran una clase incrustada (derivada `XSampleConnPt` de `CConnectionPoint`) que implementa este punto de conexión determinado. Si desea invalidar `CConnectionPoint` cualquier función miembro, o agregar funciones miembro propias, declararlas entre estas dos macros. Por ejemplo, la macro `CConnectionPoint::GetIID` CONNECTION_IID reemplaza la función miembro cuando se coloca entre estas dos macros.

El segundo fragmento de código se inserta en el archivo de implementación (. CPP) de su clase de control. Este código implementa el mapa de conexión, `SampleConnPt`que incluye el punto de conexión adicional:

[!code-cpp[NVC_MFCConnectionPoints#2](../../mfc/codesnippet/cpp/cconnectionpoint-class_2.cpp)]

Una vez insertados estos fragmentos de código, el control `ISampleSink` OLE de ejemplo expone un punto de conexión para la interfaz.

Típicamente, los puntos de conexión soportan la "multidifusión", que es la capacidad de transmitir a los receptores múltiples conectados con la misma interfaz. El siguiente fragmento de código muestra cómo realizar la multidifusión iterando a través de cada receptor en un punto de conexión:

[!code-cpp[NVC_MFCConnectionPoints#4](../../mfc/codesnippet/cpp/cconnectionpoint-class_3.cpp)]

En este ejemplo se recupera el `SampleConnPt` conjunto actual de `CConnectionPoint::GetConnections`conexiones en el punto de conexión con una llamada a . A continuación, recorre en iteración las conexiones y llama `ISampleSink::SinkFunc` a cada conexión activa.

Para obtener más `CConnectionPoint`información sobre el uso de , consulte el artículo [Puntos](../../mfc/connection-points.md)de conexión .

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CConnectionPoint`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdisp.h

## <a name="cconnectionpointcconnectionpoint"></a><a name="cconnectionpoint"></a>CConnectionPoint::CConnectionPoint

Construye un objeto `CConnectionPoint`.

```
CConnectionPoint();
```

## <a name="cconnectionpointgetconnections"></a><a name="getconnections"></a>CConnectionPoint::GetConnections

Llame a esta función para recuperar todas las conexiones activas para un punto de conexión.

```
const CPtrArray* GetConnections();
```

### <a name="return-value"></a>Valor devuelto

Puntero a una matriz de conexiones activas (sumideros). Algunos de los punteros de la matriz pueden ser NULL. Cada puntero no NULL de esta matriz se puede convertir de forma segura en un puntero a la interfaz de receptor mediante un operador de conversión.

## <a name="cconnectionpointgetcontainer"></a><a name="getcontainer"></a>CConnectionPoint::GetContainer

Llamado por el marco `IConnectionPointContainer` de trabajo para recuperar el punto de conexión para.

```
virtual LPCONNECTIONPOINTCONTAINER GetContainer();
```

### <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, un puntero al contenedor; NULL.

### <a name="remarks"></a>Observaciones

Esta función normalmente se implementa mediante la macro BEGIN_CONNECTION_PART.

## <a name="cconnectionpointgetiid"></a><a name="getiid"></a>CConnectionPoint::GetIID

Llamado por el marco de trabajo para recuperar el identificador de interfaz de un punto de conexión.

```
virtual REFIID GetIID() = 0;
```

### <a name="return-value"></a>Valor devuelto

Una referencia al ID de interfaz del punto de conexión.

### <a name="remarks"></a>Observaciones

Invalide esta función para devolver el identificador de interfaz para este punto de conexión.

## <a name="cconnectionpointgetmaxconnections"></a><a name="getmaxconnections"></a>CConnectionPoint::GetMaxConnections

Llamado por el marco de trabajo para recuperar el número máximo de conexiones admitidas por el punto de conexión.

```
virtual int GetMaxConnections();
```

### <a name="return-value"></a>Valor devuelto

El número máximo de conexiones admitidas por el control, o -1 si no hay límite.

### <a name="remarks"></a>Observaciones

La implementación predeterminada devuelve -1, lo que indica que no hay límite.

Invalide esta función si desea limitar el número de receptores que se pueden conectar al control.

## <a name="cconnectionpointgetnextconnection"></a><a name="getnextconnection"></a>CConnectionPoint::GetNextConnection

Recupera un puntero al elemento de conexión en *pos*.

```
LPUNKNOWN GetNextConnection(POSITION& pos) const;
```

### <a name="parameters"></a>Parámetros

*Pos*<br/>
Especifica una referencia a un POSITION `GetNextConnection` valor devuelto por una llamada anterior o [GetStartPosition.](#getstartposition)

### <a name="return-value"></a>Valor devuelto

Un puntero al elemento de conexión especificado por *pos*, o NULL.

### <a name="remarks"></a>Observaciones

Esta función es más útil para recorrer en iteración todos los elementos del mapa de conexión. Al iterar, omita los NULL devueltos de esta función.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCConnectionPoints#4](../../mfc/codesnippet/cpp/cconnectionpoint-class_3.cpp)]

## <a name="cconnectionpointgetstartposition"></a><a name="getstartposition"></a>CConnectionPoint::GetStartPosition

Inicia una iteración de mapa devolviendo un valor POSITION que se puede pasar a una llamada [GetNextConnection.](#getnextconnection)

```
POSITION GetStartPosition() const;
```

### <a name="return-value"></a>Valor devuelto

Un valor POSITION que indica una posición inicial para iterar el mapa; null si el mapa está vacío.

### <a name="remarks"></a>Observaciones

La secuencia de iteración no es predecible; por lo tanto, el "primer elemento en el mapa" no tiene un significado especial.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CConnectionPoint::GetNextConnection](#getnextconnection).

## <a name="cconnectionpointonadvise"></a><a name="onadvise"></a>CConnectionPoint::OnAdvise

Llamado por el marco de trabajo cuando se establece o se rompe una conexión.

```
virtual void OnAdvise(BOOL bAdvise);
```

### <a name="parameters"></a>Parámetros

*bAdvise*<br/>
TRUE, si se está estableciendo una conexión; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

La implementación predeterminada no hace nada.

Reemplace esta función si desea una notificación cuando los receptores se conectan o se desconectan del punto de conexión.

## <a name="cconnectionpointquerysinkinterface"></a><a name="querysinkinterface"></a>CConnectionPoint::QuerySinkInterface

Recupera un puntero a la interfaz de receptor solicitada.

```
virtual HRESULT QuerySinkInterface(
    LPUNKNOWN pUnkSink,
    void** ppInterface);
```

### <a name="parameters"></a>Parámetros

*pUnkSink*<br/>
Identificador de la interfaz de receptor que se solicita.

*ppInterface*<br/>
Puntero al puntero de interfaz identificado por *pUnkSink*. Si el objeto no admite \* esta interfaz, *ppInterface* se establece en NULL.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

## <a name="see-also"></a>Consulte también

[CCmdTarget (clase)](../../mfc/reference/ccmdtarget-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
