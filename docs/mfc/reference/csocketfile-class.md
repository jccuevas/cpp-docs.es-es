---
title: CSocketFile (clase)
ms.date: 11/04/2016
f1_keywords:
- CSocketFile
- AFXSOCK/CSocketFile
- AFXSOCK/CSocketFile::CSocketFile
helpviewer_keywords:
- CSocketFile [MFC], CSocketFile
ms.assetid: 7924c098-5f72-40d6-989d-42800a47958f
ms.openlocfilehash: f3fa73320ae34283b0cdac559111a53a879c031c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62324056"
---
# <a name="csocketfile-class"></a>CSocketFile (clase)

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

Puede adjuntar el `CSocketFile` objeto a un `CSocket` objeto para este propósito. También puede y normalmente, adjunte el `CSocketFile` objeto a un `CArchive` objeto para simplificar, enviar y recibir datos utilizando la serialización de MFC.

Para serializar los datos (envío), lo inserta en el archivo, que llama a `CSocketFile` funciones miembro para escribir datos en el `CSocket` objeto. Para deserializar (recepción) datos, extraer desde el archivo. Esto hace que el archivo llamar a `CSocketFile` funciones miembro para leer datos desde el `CSocket` objeto.

> [!TIP]
>  Además de usar `CSocketFile` como se describe aquí, puede usarlo como un objeto de archivo independiente, se puede hacer con `CFile`, su clase base. También puede usar `CSocketFile` con las funciones de serialización de MFC basada en el almacenamiento. Dado que `CSocketFile` no admite todos `CFile`de la funcionalidad, algún valor predeterminado MFC serializar funciones no son compatibles con `CSocketFile`. Esto es particularmente cierto con las `CEditView` clase. No debe intentar serializar `CEditView` datos a través de un `CArchive` objeto asociado a un `CSocketFile` objeto mediante `CEditView::SerializeRaw`; use `CEditView::Serialize` en su lugar. El `SerializeRaw` función espera tener funciones, como el objeto de archivo `Seek`, que `CSocketFile` no tiene.

Cuando usas `CArchive` con `CSocketFile` y `CSocket`, pueda encontrar una situación donde `CSocket::Receive` entra en un bucle (por `PumpMessages(FD_READ)`) a la espera para la cantidad de bytes solicitada. Esto es debido a que los sockets de Windows permiten sólo una llamada de recepción por notificación FD_READ, pero `CSocketFile` y `CSocket` permitir varias llamadas recibidas por FD_READ. Si recibe un FD_READ cuando no hay ningún dato para leer, la aplicación se bloquea. Si nunca se produce otra FD_READ, la aplicación deja de comunicarse a través del socket.

Puede resolver este problema como se indica a continuación. En el `OnReceive` método de la clase socket, llamada `CAsyncSocket::IOCtl(FIONREAD, ...)` antes de llamar a la `Serialize` método de la clase de mensaje cuando los datos esperados para leerse desde el socket superan el tamaño de un paquete TCP (unidad de transmisión máxima del medio de red Normalmente, al menos 1096 bytes). Si el tamaño de los datos disponibles es menor que el necesario, espere a todos los datos se reciben y solo después inicia la operación de lectura.

En el ejemplo siguiente, `m_dwExpected` es el número aproximado de bytes que el usuario espera recibir. Se supone que se declara en otra parte en el código.

[!code-cpp[NVC_MFCSocketThread#4](../../mfc/reference/codesnippet/cpp/csocketfile-class_1.cpp)]

Para obtener más información, consulte [Windows Sockets en MFC](../../mfc/windows-sockets-in-mfc.md), [Windows Sockets: Usar Sockets con archivos](../../mfc/windows-sockets-using-sockets-with-archives.md), así como [API de Windows Sockets 2](/windows/desktop/WinSock/windows-sockets-start-page-2).

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

*pSocket*<br/>
El socket para adjuntar a la `CSocketFile` objeto.

*bArchiveCompatible*<br/>
Especifica si el objeto de archivo es para su uso con un `CArchive` objeto. Pase FALSE solo si desea usar el `CSocketFile` objeto de forma independiente como lo haría una independiente `CFile` objeto, con ciertas limitaciones. Esta marca se cambia el modo `CArchive` objeto asociado al `CSocketFile` objeto administra su búfer de lectura.

### <a name="remarks"></a>Comentarios

El destructor del objeto se desasocia propio desde el objeto de socket cuando se sale del ámbito o se elimina el objeto.

> [!NOTE]
>  Un `CSocketFile` también puede usarse como un archivo (limitado) sin un `CArchive` objeto. De forma predeterminada, el `CSocketFile` del constructor *bArchiveCompatible* parámetro es TRUE. Esto especifica que el objeto de archivo es para su uso con un archivo. Para usar el objeto de archivo sin un archivo, pase FALSE en el *bArchiveCompatible* parámetro.

En el modo "compatible con el archivo", un `CSocketFile` objeto proporciona un mejor rendimiento y reduce el riesgo de "interbloqueo". Un interbloqueo se produce cuando los sockets envío y recepción están esperando mutuamente, o para un recurso común. Esto puede suceder si el `CArchive` objeto trabajó con el `CSocketFile` el modo en que lo hace con un `CFile` objeto. Con `CFile`, el archivo puede suponer que si recibe menos bytes que los solicitados, se ha alcanzado el final del archivo.

Con `CSocketFile`, sin embargo, están de datos basado en mensajes; el búfer puede contener varios mensajes, por lo que recibe menos que el número de bytes solicitado no implica el final del archivo. La aplicación no se bloquea en este caso, como podría ocurrir con `CFile`, y puede continuar leyendo mensajes desde el búfer hasta que el búfer está vacío. El [CArchive::IsBufferEmpty](../../mfc/reference/carchive-class.md#isbufferempty) función es útil para supervisar el estado del búfer del archivo en este caso.

Para obtener más información sobre el uso de `CSocketFile`, consulte los artículos [Windows Sockets: Usar Sockets con archivos](../../mfc/windows-sockets-using-sockets-with-archives.md) y [Windows Sockets: Ejemplo de Sockets que usan archivos](../../mfc/windows-sockets-example-of-sockets-using-archives.md).

## <a name="see-also"></a>Vea también

[CFile (clase)](../../mfc/reference/cfile-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CAsyncSocket (clase)](../../mfc/reference/casyncsocket-class.md)<br/>
[CSocket (clase)](../../mfc/reference/csocket-class.md)
