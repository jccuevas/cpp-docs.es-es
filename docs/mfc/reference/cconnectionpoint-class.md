---
title: Clase de CConnectionPoint | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CConnectionPoint
dev_langs:
- C++
helpviewer_keywords:
- CConnectionPoint class
ms.assetid: f0f23a1e-5e8c-41a9-aa6c-1a4793b28e8f
caps.latest.revision: 20
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
ms.openlocfilehash: a511f252bf921433d070059518e6e67b952680eb
ms.lasthandoff: 02/24/2017

---
# <a name="cconnectionpoint-class"></a>Clase de CConnectionPoint
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
|[CConnectionPoint:: GetConnections](#getconnections)|Recupera todos los puntos de conexión en un mapa de conexión.|  
|[CConnectionPoint::GetContainer](#getcontainer)|Recupera el contenedor del control que posee el mapa de conexión.|  
|[CConnectionPoint:: GetIID](#getiid)|Recupera el identificador de interfaz de un punto de conexión.|  
|[CConnectionPoint::GetMaxConnections](#getmaxconnections)|Recupera el número máximo de puntos de conexión que admite un control.|  
|[CConnectionPoint:: GetNextConnection](#getnextconnection)|Recupera un puntero al elemento de la conexión `pos`.|  
|[CConnectionPoint::GetStartPosition](#getstartposition)|Inicia una iteración de mapa devolviendo un **posición** valor que se puede pasar a un `GetNextConnection` llamar.|  
|[CConnectionPoint::OnAdvise](#onadvise)|Llamado por el marco al establecer o interrumpir las conexiones.|  
|[CConnectionPoint::QuerySinkInterface](#querysinkinterface)|Recupera un puntero a la interfaz de receptor solicitado.|  
  
## <a name="remarks"></a>Comentarios  
 A diferencia de las interfaces OLE normales, que se utilizan para implementar y exponer la funcionalidad de un control OLE, un punto de conexión implementa una interfaz de salida que puede iniciar acciones de otros objetos, como activar eventos y notificaciones de cambio.  
  
 Una conexión que consta de dos partes: el objeto llamando a la interfaz denominada "origen" y el objeto que implementa la interfaz, denominada "receptor". Al exponer un punto de conexión, un origen permite a los receptores establecer conexiones a sí mismo. A través del mecanismo de punto de conexión, un objeto de origen Obtiene un puntero a la implementación del receptor de un conjunto de funciones miembro. Por ejemplo, para desencadenar un evento implementado por el receptor, el origen puede llamar al método correspondiente de la implementación del receptor.  
  
 De forma predeterminada, un `COleControl`-clase derivada implementa dos puntos de conexión: uno para eventos y otro para la propiedad de las notificaciones de cambio. Estas conexiones se utilizan, respectivamente, para el desencadenamiento de eventos y para notificar a un receptor (por ejemplo, el contenedor del control) cuando un valor de propiedad ha cambiado. También se proporciona compatibilidad para que controles OLE implementar puntos de conexión adicionales. Para cada punto de conexión adicionales implementado en la clase del control, se debe declarar un "elemento de conexión" que implementa el punto de conexión. Si implementa uno o varios puntos de conexión, debe declarar un único "mapa de conexión" en la clase del control.  
  
 En el ejemplo siguiente se muestra un mapa de conexión simple y un punto de conexión para el `Sample` control OLE, que consta de dos fragmentos de código: la primera parte declara el mapa de conexión y el punto; el segundo implementa este mapa y el punto. El primer fragmento se inserta en la declaración de la clase de control, en la `protected` sección:  
  
 [!code-cpp[NVC_MFCConnectionPoints&#7;](../../mfc/codesnippet/cpp/cconnectionpoint-class_1.h)]  
  
 El `BEGIN_CONNECTION_PART` y `END_CONNECTION_PART` declaran una clase incrustada, `XSampleConnPt` (derivada de `CConnectionPoint`) que implementa este punto de conexión determinado. Si desea invalidar cualquier `CConnectionPoint` funciones miembro, o agregar funciones miembro propias, declárelas entre estas dos macros. Por ejemplo, el `CONNECTION_IID` macro reemplaza el `CConnectionPoint::GetIID` función de miembro cuando se coloca entre estas dos macros.  
  
 El segundo fragmento de código se inserta en el archivo de implementación (. (CPP) de la clase del control. Este código implementa el mapa de conexión, que incluye el punto de conexión adicionales, `SampleConnPt`:  
  
 [!code-cpp[NVC_MFCConnectionPoints&#2;](../../mfc/codesnippet/cpp/cconnectionpoint-class_2.cpp)]  
  
 Una vez que se han insertado estos fragmentos de código, el control de ejemplo OLE expone un punto de conexión para la **ISampleSink** interfaz.  
  
 Normalmente, los puntos de conexión aceptan "multidifusión", que es la capacidad para difundir a varios receptores conectados a la misma interfaz. El fragmento de código siguiente muestra cómo realizar la multidifusión recorriendo en iteración cada receptor en un punto de conexión:  
  
 [!code-cpp[NVC_MFCConnectionPoints Nº&4;](../../mfc/codesnippet/cpp/cconnectionpoint-class_3.cpp)]  
  
 Este ejemplo recupera el conjunto actual de conexiones en el `SampleConnPt` punto de conexión con una llamada a `CConnectionPoint::GetConnections`. A continuación, recorre en iteración las conexiones y las llamadas `ISampleSink::SinkFunc` en todas las conexiones activas.  
  
 Para obtener más información sobre el uso de `CConnectionPoint`, vea el artículo [puntos de conexión](../../mfc/connection-points.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CConnectionPoint`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdisp.h  
  
##  <a name="a-namecconnectionpointa--cconnectionpointcconnectionpoint"></a><a name="cconnectionpoint"></a>CConnectionPoint::CConnectionPoint  
 Construye un objeto `CConnectionPoint`.  
  
```  
CConnectionPoint();
```  
  
##  <a name="a-namegetconnectionsa--cconnectionpointgetconnections"></a><a name="getconnections"></a>CConnectionPoint:: GetConnections  
 Llame a esta función para recuperar todas las conexiones activas de un punto de conexión.  
  
```  
const CPtrArray* GetConnections();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a una matriz de conexiones activas (receptores). Algunos de los punteros de la matriz pueden ser NULL. Cada puntero no NULL en esta matriz se puede convertir de forma segura a un puntero a la interfaz de receptor con un operador de conversión.  
  
##  <a name="a-namegetcontainera--cconnectionpointgetcontainer"></a><a name="getcontainer"></a>CConnectionPoint::GetContainer  
 Llamado por el marco para recuperar la **IConnectionPointContainer** para el punto de conexión.  
  
```  
virtual LPCONNECTIONPOINTCONTAINER GetContainer();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, un puntero al contenedor; de lo contrario, **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Esta función normalmente se implementa mediante el `BEGIN_CONNECTION_PART` (macro).  
  
##  <a name="a-namegetiida--cconnectionpointgetiid"></a><a name="getiid"></a>CConnectionPoint:: GetIID  
 Llamado por el marco de trabajo para recuperar el identificador de interfaz de un punto de conexión.  
  
```  
virtual REFIID GetIID() = 0;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia al identificador de interfaz. del punto de conexión  
  
### <a name="remarks"></a>Comentarios  
 Reemplazar esta función para devolver el identificador de interfaz de este punto de conexión.  
  
##  <a name="a-namegetmaxconnectionsa--cconnectionpointgetmaxconnections"></a><a name="getmaxconnections"></a>CConnectionPoint::GetMaxConnections  
 Llamado por el marco de trabajo para recuperar el número máximo de conexiones admitidas por el punto de conexión.  
  
```  
virtual int GetMaxConnections();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número máximo de conexiones admitido por el control, o -1 si no hay ningún límite.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada devuelve -1, que indica ningún límite.  
  
 Reemplace esta función si desea limitar el número de receptores a los que puede conectarse a su control.  
  
##  <a name="a-namegetnextconnectiona--cconnectionpointgetnextconnection"></a><a name="getnextconnection"></a>CConnectionPoint:: GetNextConnection  
 Recupera un puntero al elemento de la conexión `pos`.  
  
```  
LPUNKNOWN GetNextConnection(POSITION& pos) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `pos`  
 Especifica una referencia a un **posición** valor devuelto por un método `GetNextConnection` o [GetStartPosition](#getstartposition) llamar.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al elemento de conexión especificado por `pos`, o NULL.  
  
### <a name="remarks"></a>Comentarios  
 Esta función es muy útil para recorrer en iteración todos los elementos en el mapa de conexión. Al recorrer en iteración, omita los valores NULL devueltos por esta función.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCConnectionPoints Nº&4;](../../mfc/codesnippet/cpp/cconnectionpoint-class_3.cpp)]  
  
##  <a name="a-namegetstartpositiona--cconnectionpointgetstartposition"></a><a name="getstartposition"></a>CConnectionPoint::GetStartPosition  
 Inicia una iteración de mapa devolviendo un **posición** valor que se puede pasar a un [GetNextConnection](#getnextconnection) llamar.  
  
```  
POSITION GetStartPosition() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un **posición** valor que indica la posición de comienzo para recorrer en iteración el mapa; o **NULL** si el mapa está vacío.  
  
### <a name="remarks"></a>Comentarios  
 La secuencia de la iteración no es de predicción; por lo tanto, el "primer elemento en el mapa" no tiene especial importancia.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CConnectionPoint:: GetNextConnection](#getnextconnection).  
  
##  <a name="a-nameonadvisea--cconnectionpointonadvise"></a><a name="onadvise"></a>CConnectionPoint::OnAdvise  
 Llamado por el marco cuando una conexión es el que se establece o se interrumpe.  
  
```  
virtual void OnAdvise(BOOL bAdvise);
```  
  
### <a name="parameters"></a>Parámetros  
 `bAdvise`  
 **TRUE**, si una conexión está establecida; de lo contrario **FALSE**.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada no hace nada.  
  
 Reemplace esta función si desea notificaciones cuando los receptores de conexión o desconexión desde el punto de conexión.  
  
##  <a name="a-namequerysinkinterfacea--cconnectionpointquerysinkinterface"></a><a name="querysinkinterface"></a>CConnectionPoint::QuerySinkInterface  
 Recupera un puntero a la interfaz de receptor solicitado.  
  
```  
virtual HRESULT QuerySinkInterface(
    LPUNKNOWN pUnkSink,  
    void** ppInterface);
```  
  
### <a name="parameters"></a>Parámetros  
 `pUnkSink`  
 El identificador de la interfaz de receptor que se solicita.  
  
 `ppInterface`  
 Un puntero al puntero de interfaz identificado por `pUnkSink`. Si el objeto no admite esta interfaz, \* `ppInterface` está establecido en **NULL**.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
## <a name="see-also"></a>Vea también  
 [CCmdTarget (clase)](../../mfc/reference/ccmdtarget-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)


