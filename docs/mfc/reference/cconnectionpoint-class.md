---
title: Clase de CConnectionPoint | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d892ea225e3b1c1089447587eb808e56370bbb69
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/26/2018
ms.locfileid: "36952227"
---
# <a name="cconnectionpoint-class"></a>Clase de CConnectionPoint
Define un tipo especial de interfaz que se utiliza para comunicarse con otros objetos OLE, denominado "punto de conexión".  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CConnectionPoint : public CCmdTarget  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CConnectionPoint::CConnectionPoint](#cconnectionpoint)|Construye un objeto `CConnectionPoint`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CConnectionPoint:: GetConnections](#getconnections)|Recupera todos los puntos de conexión en un mapa de conexión.|  
|[CConnectionPoint::GetContainer](#getcontainer)|Recupera el contenedor del control que posee el mapa de conexión.|  
|[CConnectionPoint:: GetIID](#getiid)|Recupera el identificador de interfaz de un punto de conexión.|  
|[CConnectionPoint::GetMaxConnections](#getmaxconnections)|Recupera el número máximo de puntos de conexión que admite un control.|  
|[CConnectionPoint:: GetNextConnection](#getnextconnection)|Recupera un puntero al elemento de la conexión *pos*.|  
|[CConnectionPoint::GetStartPosition](#getstartposition)|Inicie una iteración de mapa devolviendo un **posición** valor que se puede pasar a un `GetNextConnection` llamar a.|  
|[CConnectionPoint::OnAdvise](#onadvise)|Lo llama el marco al establecer o interrumpir las conexiones.|  
|[CConnectionPoint::QuerySinkInterface](#querysinkinterface)|Recupera un puntero a la interfaz del receptor solicitado.|  
  
## <a name="remarks"></a>Comentarios  
 A diferencia de las interfaces OLE normales, que se usan para implementar y exponer la funcionalidad de un control OLE, un punto de conexión implementa una interfaz de salida que es capaz de iniciar acciones de otros objetos, como desencadenar eventos y notificaciones de cambio.  
  
 Una conexión consta de dos partes: el objeto de una llamada a la interfaz, denominada "origen" y el objeto que implementa la interfaz, denominada "receptor". Al exponer un punto de conexión, un origen permite a los receptores establecer conexiones a sí mismo. A través del mecanismo de punto de conexión, un objeto de origen Obtiene un puntero a la implementación del receptor de un conjunto de funciones miembro. Por ejemplo, para desencadenar un evento implementado por el receptor, el origen puede llamar al método correspondiente de la implementación del receptor.  
  
 De forma predeterminada, un `COleControl`-clase derivada implementa dos puntos de conexión: uno para eventos y otro para la propiedad de las notificaciones de cambio. Estas conexiones se utilizan, respectivamente, para la activación de eventos y para notificar a un receptor (por ejemplo, el contenedor del control) cuando un valor de propiedad ha cambiado. También se proporciona compatibilidad para que controles OLE implementar puntos de conexión adicionales. Para cada punto de conexión adicionales que se implementa en la clase del control, se debe declarar una "parte de la conexión" que implementa el punto de conexión. Si implementa uno o varios puntos de conexión, debe declarar un único "mapa de conexión" en la clase del control.  
  
 En el ejemplo siguiente se muestra un mapa de conexión simple y un punto de conexión para el `Sample` control OLE, que consta de dos fragmentos de código: la primera parte declara el mapa de conexión y el punto; el segundo implementa este mapa y el punto. El primer fragmento se inserta en la declaración de la clase de control, en la `protected` sección:  
  
 [!code-cpp[NVC_MFCConnectionPoints#7](../../mfc/codesnippet/cpp/cconnectionpoint-class_1.h)]  
  
 Las macros BEGIN_CONNECTION_PART y END_CONNECTION_PART declaran una clase incrustada, `XSampleConnPt` (derivado de `CConnectionPoint`) que implementa este punto de conexión determinado. Si desea invalidar cualquier `CConnectionPoint` funciones miembro, o agregar funciones miembro de su elección, declárelos entre estas dos macros. Por ejemplo, la macro CONNECTION_IID reemplaza el `CConnectionPoint::GetIID` función de miembro al que se encuentra entre estas dos macros.  
  
 El segundo fragmento de código se inserta en el archivo de implementación (. CPP) de la clase del control. Este código implementa el mapa de conexión, que incluye el punto de conexión adicionales, `SampleConnPt`:  
  
 [!code-cpp[NVC_MFCConnectionPoints#2](../../mfc/codesnippet/cpp/cconnectionpoint-class_2.cpp)]  
  
 Una vez que se han insertado estos fragmentos de código, el control OLE de ejemplo expone un punto de conexión para el `ISampleSink` interfaz.  
  
 Por lo general, los puntos de conexión aceptan "multidifusión", que es la capacidad para difundir a varios receptores conectados a la misma interfaz. El fragmento de código siguiente muestra cómo llevar a cabo la multidifusión recorriendo en iteración cada receptor en un punto de conexión:  
  
 [!code-cpp[NVC_MFCConnectionPoints#4](../../mfc/codesnippet/cpp/cconnectionpoint-class_3.cpp)]  
  
 Este ejemplo recupera el conjunto actual de conexiones en el `SampleConnPt` punto de conexión con una llamada a `CConnectionPoint::GetConnections`. A continuación, recorre las conexiones y las llamadas `ISampleSink::SinkFunc` en todas las conexiones activas.  
  
 Para obtener más información sobre el uso de `CConnectionPoint`, vea el artículo [puntos de conexión](../../mfc/connection-points.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CConnectionPoint`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdisp.h  
  
##  <a name="cconnectionpoint"></a>  CConnectionPoint::CConnectionPoint  
 Construye un objeto `CConnectionPoint`.  
  
```  
CConnectionPoint();
```  
  
##  <a name="getconnections"></a>  CConnectionPoint:: GetConnections  
 Llame a esta función para recuperar todas las conexiones activas para un punto de conexión.  
  
```  
const CPtrArray* GetConnections();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a una matriz de conexiones activas (receptores). Algunos de los punteros de la matriz pueden ser NULL. Cada puntero no NULL en esta matriz se puede convertir de forma segura en un puntero a la interfaz del receptor con un operador de conversión.  
  
##  <a name="getcontainer"></a>  CConnectionPoint::GetContainer  
 Lo llama el marco para recuperar el **IConnectionPointContainer** para el punto de conexión.  
  
```  
virtual LPCONNECTIONPOINTCONTAINER GetContainer();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, un puntero al contenedor; en caso contrario, **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Esta función normalmente se implementa mediante la macro BEGIN_CONNECTION_PART.  
  
##  <a name="getiid"></a>  CConnectionPoint:: GetIID  
 Lo llama el marco de trabajo para recuperar el identificador de interfaz de un punto de conexión.  
  
```  
virtual REFIID GetIID() = 0;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia al identificador de interfaz. del punto de conexión  
  
### <a name="remarks"></a>Comentarios  
 Reemplace esta función para devolver el identificador de interfaz para este punto de conexión.  
  
##  <a name="getmaxconnections"></a>  CConnectionPoint::GetMaxConnections  
 Lo llama el marco de trabajo para recuperar el número máximo de conexiones compatibles con el punto de conexión.  
  
```  
virtual int GetMaxConnections();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número máximo de conexiones admitido por el control, o -1 si no hay ningún límite.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada devuelve -1, que indica sin límite.  
  
 Reemplace esta función si desea limitar el número de receptores a los que puede conectarse a su control.  
  
##  <a name="getnextconnection"></a>  CConnectionPoint:: GetNextConnection  
 Recupera un puntero al elemento de la conexión *pos*.  
  
```  
LPUNKNOWN GetNextConnection(POSITION& pos) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 *punto de venta*  
 Especifica una referencia a un **posición** valor devuelto por un anterior `GetNextConnection` o [GetStartPosition](#getstartposition) llamar.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al elemento de conexión especificado por *pos*, o NULL.  
  
### <a name="remarks"></a>Comentarios  
 Esta función es muy útil para recorrer en iteración todos los elementos en el mapa de conexión. Cuando se itera, omite los valores NULL devueltos por esta función.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCConnectionPoints#4](../../mfc/codesnippet/cpp/cconnectionpoint-class_3.cpp)]  
  
##  <a name="getstartposition"></a>  CConnectionPoint::GetStartPosition  
 Inicie una iteración de mapa devolviendo un **posición** valor que puede pasarse a una [GetNextConnection](#getnextconnection) llamar a.  
  
```  
POSITION GetStartPosition() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 A **posición** valor que indica una posición inicial para efectuar una iteración del objeto map; o **NULL** si el mapa está vacío.  
  
### <a name="remarks"></a>Comentarios  
 La secuencia de la iteración no es de predicción; por lo tanto, el "primer elemento en el mapa" no tiene ninguna importancia especial.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CConnectionPoint:: GetNextConnection](#getnextconnection).  
  
##  <a name="onadvise"></a>  CConnectionPoint::OnAdvise  
 Lo llama el marco cuando la conexión es que se va a establecer o se ha roto.  
  
```  
virtual void OnAdvise(BOOL bAdvise);
```  
  
### <a name="parameters"></a>Parámetros  
 *bAdvise*  
 **TRUE**, si una conexión se está establecida; de lo contrario **FALSE**.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada no hace nada.  
  
 Reemplace esta función si desea notificación cuando receptores conectan o desconexión desde el punto de conexión.  
  
##  <a name="querysinkinterface"></a>  CConnectionPoint::QuerySinkInterface  
 Recupera un puntero a la interfaz del receptor solicitado.  
  
```  
virtual HRESULT QuerySinkInterface(
    LPUNKNOWN pUnkSink,  
    void** ppInterface);
```  
  
### <a name="parameters"></a>Parámetros  
 *pUnkSink*  
 El identificador de la interfaz del receptor que se solicita.  
  
 *ppInterface*  
 Un puntero al puntero de interfaz identificado por *pUnkSink*. Si el objeto no admite esta interfaz, \* *ppInterface* está establecido en **NULL**.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
## <a name="see-also"></a>Vea también  
 [CCmdTarget (clase)](../../mfc/reference/ccmdtarget-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)

