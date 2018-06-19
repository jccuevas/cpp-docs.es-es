---
title: Clase CSocketFile | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CSocketFile
- AFXSOCK/CSocketFile
- AFXSOCK/CSocketFile::CSocketFile
dev_langs:
- C++
helpviewer_keywords:
- CSocketFile [MFC], CSocketFile
ms.assetid: 7924c098-5f72-40d6-989d-42800a47958f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0e3bf8d9ee58143e7a96b85174e4533b3c2e50ec
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33372640"
---
# <a name="csocketfile-class"></a>Clase CSocketFile
Se utiliza un objeto `CFile` para enviar y recibir datos a través de una red mediante Windows Sockets.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CSocketFile : public CFile  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSocketFile::CSocketFile](#csocketfile)|Construye un objeto `CSocketFile`.|  
  
## <a name="remarks"></a>Comentarios  
 Puede adjuntar el `CSocketFile` el objeto a un `CSocket` objeto para este propósito. También puede realizar y, normalmente, adjuntar la `CSocketFile` el objeto a un `CArchive` objeto para simplificar el envío y recepción de datos usa la serialización de MFC.  
  
 Para serializar datos (envío), insértela en el archivo, que llama `CSocketFile` funciones de miembro para escribir datos en el `CSocket` objeto. Para deserializar (recepción) datos, extraer del archivo. Esto hace que el archivo llamar a `CSocketFile` funciones miembro para leer los datos de la `CSocket` objeto.  
  
> [!TIP]
>  Además de usar `CSocketFile` tal como se describe a continuación, utilizarla como un objeto de archivo independiente, igual que lo haría con `CFile`, su clase base. También puede usar `CSocketFile` con cualquier función de serialización de MFC basado en archivo. Dado que `CSocketFile` no admitir todas `CFile`de funcionalidad, algunos predeterminado MFC serializar funciones no son compatibles con `CSocketFile`. Esto es especialmente así la `CEditView` clase. No debe intentar serializar `CEditView` datos a través de un `CArchive` objeto asociado a un `CSocketFile` objeto mediante la `CEditView::SerializeRaw`; use **CEditView** en su lugar. El `SerializeRaw` función espera el objeto de archivo tenga funciones, como `Seek`, que `CSocketFile` no tiene.  
  
 Cuando usas `CArchive` con `CSocketFile` y `CSocket`, puede darse el caso donde **CSocket::Receive** entra en un bucle (por **PumpMessages(FD_READ)**) esperando el cantidad de bytes solicitada. Esto es porque Windows sockets permite sólo una llamada de recepción por la notificación de FD_READ, pero `CSocketFile` y `CSocket` permitir varias llamadas de recepción por FD_READ. Si recibe un FD_READ cuando no hay datos para leer, la aplicación se bloquea. Si nunca se produce otro FD_READ, la aplicación deja de comunicarse a través del socket.  
  
 Puede resolver este problema como se indica a continuación. En el `OnReceive` método de la clase socket, llamada **CAsyncSocket::IOCtl (FIONREAD,...)**  antes de llamar a la `Serialize` método de la clase de mensaje cuando los datos esperados para leer desde el socket superan el tamaño de un paquete TCP (unidad de transmisión máxima del medio de red, normalmente por lo menos 1096 bytes). Si el tamaño de los datos disponibles es menor que el necesario, espere a todos los datos que puede recibir y luego iniciar la operación de lectura.  
  
 En el ejemplo siguiente, `m_dwExpected` es el número aproximado de bytes que el usuario espera recibir. Se supone que se declara en otra parte en el código.  
  
 [!code-cpp[NVC_MFCSocketThread#4](../../mfc/reference/codesnippet/cpp/csocketfile-class_1.cpp)]  
  
 Para obtener más información, consulte [Windows Sockets en MFC](../../mfc/windows-sockets-in-mfc.md), [Windows Sockets: usar Sockets con archivos](../../mfc/windows-sockets-using-sockets-with-archives.md), así como [API de Windows Sockets 2](http://msdn.microsoft.com/library/windows/desktop/ms740673).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 `CSocketFile`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxsock.h  
  
##  <a name="csocketfile"></a>  CSocketFile::CSocketFile  
 Construye un objeto `CSocketFile`.  
  
```  
explicit CSocketFile(
    CSocket* pSocket,  
    BOOL bArchiveCompatible = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `pSocket`  
 El socket para adjuntar a la `CSocketFile` objeto.  
  
 `bArchiveCompatible`  
 Especifica si el objeto de archivo es para su uso con un `CArchive` objeto. Pasar **FALSE** únicamente si desea utilizar el `CSocketFile` objeto de forma independiente como lo haría con un `CFile` objeto, con ciertas limitaciones. Esta marca cambia cómo el `CArchive` objeto asociado a la `CSocketFile` objeto administra su búfer para su lectura.  
  
### <a name="remarks"></a>Comentarios  
 Al destructor del objeto se desasocia propia del objeto de socket cuando el objeto queda fuera del ámbito o se elimina.  
  
> [!NOTE]
>  A `CSocketFile` también puede usarse como un archivo (limitado) sin un `CArchive` objeto. De forma predeterminada, el `CSocketFile` del constructor `bArchiveCompatible` parámetro es **TRUE**. Esto especifica que el objeto de archivo es para su uso con un archivo. Para usar el objeto de archivo sin un archivo, pase **FALSE** en el `bArchiveCompatible` parámetro.  
  
 En el modo "compatible con el archivo", un `CSocketFile` objeto proporciona un mejor rendimiento y reduce el riesgo de un "interbloqueo". Un interbloqueo se produce cuando los sockets envío y recepción se esperan entre sí, o para un recurso común. Esto puede suceder si el `CArchive` objeto ha trabajado con la `CSocketFile` el modo en que lo hace con un `CFile` objeto. Con `CFile`, el archivo puede suponer que si recibe menos bytes que los solicitados, se ha alcanzado el final del archivo.  
  
 Con `CSocketFile`, sin embargo, están de datos basado en mensajes; el búfer puede contener varios mensajes, por lo que recibir menor que el número de bytes solicitado no implica el final del archivo. La aplicación no se bloquea en este caso, como podría ocurrir con `CFile`, y puede seguir leyendo mensajes del búfer hasta que el búfer está vacío. El [CArchive::IsBufferEmpty](../../mfc/reference/carchive-class.md#isbufferempty) función es útil para supervisar el estado del búfer del archivo en este caso.  
  
 Para obtener más información sobre el uso de `CSocketFile`, consulte los artículos [Windows Sockets: usar Sockets con archivos](../../mfc/windows-sockets-using-sockets-with-archives.md) y [Windows Sockets: ejemplo de Sockets con archivos](../../mfc/windows-sockets-example-of-sockets-using-archives.md).  
  
## <a name="see-also"></a>Vea también  
 [CFile (clase)](../../mfc/reference/cfile-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CAsyncSocket (clase)](../../mfc/reference/casyncsocket-class.md)   
 [CSocket (clase)](../../mfc/reference/csocket-class.md)
