---
title: Clase CSocketFile | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSocketFile
- AFXSOCK/CSocketFile
- AFXSOCK/CSocketFile::CSocketFile
dev_langs:
- C++
helpviewer_keywords:
- networks [C++], archive
- serialization [C++], network
- networks [C++], serializing to
- CSocketFile class
- archives [C++], network
- SOCKET handle
ms.assetid: 7924c098-5f72-40d6-989d-42800a47958f
caps.latest.revision: 24
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
ms.openlocfilehash: 6ca331c07e0a9fc48f152042fcccd5c38e743ccf
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="csocketfile-class"></a>Clase CSocketFile
Se utiliza un objeto `CFile` para enviar y recibir datos a través de una red mediante Windows Sockets.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CSocketFile : public CFile  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CSocketFile::CSocketFile](#csocketfile)|Construye un objeto `CSocketFile`.|  
  
## <a name="remarks"></a>Comentarios  
 Puede adjuntar el `CSocketFile` objeto un `CSocket` objeto para este propósito. También puede y normalmente, adjuntar la `CSocketFile` objeto un `CArchive` objeto para simplificar el envío y recepción de datos utilizando la serialización de MFC.  
  
 Para serializar los datos (enviar), insertarlo en el archivo, que llama a `CSocketFile` funciones de miembro para escribir datos en el `CSocket` objeto. Para deserializar (recepción) datos, extraer el archivo. Esto hace que el archivo que se va a llamar a `CSocketFile` funciones de miembro para leer datos de la `CSocket` objeto.  
  
> [!TIP]
>  Además de usar `CSocketFile` tal como se describe a continuación, usarla como un objeto de archivo independiente, también se puede hacer con `CFile`, su clase base. También puede utilizar `CSocketFile` con las funciones de serialización de MFC basada en archivo. Porque `CSocketFile` no admitan todas `CFile`de funcionalidad, algunos predeterminado MFC serializar funciones no son compatibles con `CSocketFile`. Esto es especialmente cierto para la `CEditView` clase. No debe intentar serializar `CEditView` datos a través de un `CArchive` objeto asociado a un `CSocketFile` objeto mediante `CEditView::SerializeRaw`; use **CEditView** en su lugar. El `SerializeRaw` función espera el objeto de archivo tenga funciones, como `Seek`, que `CSocketFile` no tiene.  
  
 Al usar `CArchive` con `CSocketFile` y `CSocket`, puede darse el caso donde **CSocket::Receive** entra en un bucle (por **PumpMessages(FD_READ)**) esperando la cantidad de bytes solicitada. Esto es porque Windows sockets permite sólo una llamada recibidas por notificación FD_READ, pero `CSocketFile` y `CSocket` permiten varias llamadas recibidas por FD_READ. Si obtiene un FD_READ cuando no hay ningún dato que leer, se bloquea la aplicación. Si no aparece otro FD_READ nunca, la aplicación deja de comunicarse a través del socket.  
  
 Puede resolver este problema como sigue. En el `OnReceive` método de la clase socket, llamada **CAsyncSocket::IOCtl (FIONREAD,...) ** antes de llamar a la `Serialize` método de la clase de mensaje cuando los datos esperados para el socket deba leer superan el tamaño de un paquete TCP (unidad de transmisión máxima del medio de red, normalmente al menos 1096 bytes). Si el tamaño de los datos disponibles es menor que el necesario, esperar todos los datos recibir y luego iniciar la operación de lectura.  
  
 En el ejemplo siguiente, `m_dwExpected` es el número aproximado de bytes que el usuario espera recibir. Se supone que se declara en otra parte del código.  
  
 [!code-cpp[NVC_MFCSocketThread Nº&4;](../../mfc/reference/codesnippet/cpp/csocketfile-class_1.cpp)]  
  
 Para obtener más información, consulte [Windows Sockets en MFC](../../mfc/windows-sockets-in-mfc.md), [Windows Sockets: usar Sockets con archivos](../../mfc/windows-sockets-using-sockets-with-archives.md), así como [API de Windows Sockets 2](http://msdn.microsoft.com/library/windows/desktop/ms740673).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 `CSocketFile`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxsock.h  
  
##  <a name="csocketfile"></a>CSocketFile::CSocketFile  
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
 Especifica si el objeto de archivo para su uso con un `CArchive` objeto. Pasar **FALSE** sólo si desea utilizar el `CSocketFile` objeto de forma independiente como lo haría un independiente `CFile` objeto, con ciertas limitaciones. Este indicador cambia la `CArchive` objeto asociado a la `CSocketFile` objeto administra su búfer de lectura.  
  
### <a name="remarks"></a>Comentarios  
 El destructor del objeto se desasocia propio desde el objeto de socket cuando se sale del ámbito o se elimina el objeto.  
  
> [!NOTE]
>  Un `CSocketFile` también puede usarse como un archivo (limitado) sin un `CArchive` objeto. De forma predeterminada, el `CSocketFile` del constructor `bArchiveCompatible` parámetro es **TRUE**. Especifica que el objeto de archivo es para su uso con un archivo. Para utilizar el objeto de archivo sin un archivo, pase **FALSE** en el `bArchiveCompatible` parámetro.  
  
 En el modo "compatible con el archivo", un `CSocketFile` objeto proporciona un mejor rendimiento y reduce el riesgo de un "interbloqueo". Un interbloqueo se produce cuando los sockets de envío y recepción se esperan entre sí o un recurso común. Esto puede ocurrir si el `CArchive` objeto trabajó con el `CSocketFile` el modo en que lo hace con un `CFile` objeto. Con `CFile`, el archivo puede suponer que si recibe menos bytes que los solicitados, se ha alcanzado el final del archivo.  
  
 Con `CSocketFile`, sin embargo, datos están basados en mensajes; el búfer puede contener varios mensajes, por lo que recibir menos datos que el número de bytes solicitado no implica el final del archivo. La aplicación no se bloquea en este caso, como podría ocurrir con `CFile`, y podrá seguir leyendo mensajes del búfer hasta que el búfer está vacío. El [CArchive::IsBufferEmpty](../../mfc/reference/carchive-class.md#isbufferempty) función es útil para supervisar el estado del búfer del archivo de almacenamiento en este caso.  
  
 Para obtener más información sobre el uso de `CSocketFile`, consulte los artículos [Windows Sockets: usar Sockets con archivos](../../mfc/windows-sockets-using-sockets-with-archives.md) y [Windows Sockets: ejemplo de Sockets con archivos](../../mfc/windows-sockets-example-of-sockets-using-archives.md).  
  
## <a name="see-also"></a>Vea también  
 [CFile (clase)](../../mfc/reference/cfile-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [CAsyncSocket (clase)](../../mfc/reference/casyncsocket-class.md)   
 [CSocket (clase)](../../mfc/reference/csocket-class.md)

