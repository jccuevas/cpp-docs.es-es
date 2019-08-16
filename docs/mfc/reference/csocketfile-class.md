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
ms.openlocfilehash: 3b969f81c0c6e1868a66aeaa1c4d9339792062df
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502450"
---
# <a name="csocketfile-class"></a>CSocketFile (clase)

Se utiliza un objeto `CFile` para enviar y recibir datos a través de una red mediante Windows Sockets.

## <a name="syntax"></a>Sintaxis

```
class CSocketFile : public CFile
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CSocketFile::CSocketFile](#csocketfile)|Construye un objeto `CSocketFile`.|

## <a name="remarks"></a>Comentarios

Puede adjuntar `CSocketFile` el objeto a `CSocket` un objeto con este fin. También puede, y normalmente, asociar el objeto `CSocketFile` a un objeto `CArchive` para simplificar el envío y la recepción de datos mediante la serialización de MFC.

Para serializar (enviar) datos, insértelos en el archivo, que llama `CSocketFile` a las funciones miembro para escribir datos `CSocket` en el objeto. Para deserializar (recibir) datos, se extrae del archivo. Esto hace que el archivo llame `CSocketFile` a las funciones miembro para leer los `CSocket` datos del objeto.

> [!TIP]
>  Además de `CSocketFile` usar como se describe aquí, puede utilizarlo como un objeto de archivo independiente, al igual que con `CFile`, su clase base. También puede utilizar `CSocketFile` con cualquier función de serialización MFC basada en archivos. Dado `CSocketFile` que no admite toda la `CFile`funcionalidad de, algunas funciones Serialize de MFC predeterminadas no `CSocketFile`son compatibles con. Esto es especialmente cierto en la `CEditView` clase. No debe intentar `CEditView` serializar los datos a través de un `CArchive` objeto asociado `CSocketFile` a un `CEditView::SerializeRaw`objeto mediante `CEditView::Serialize` ; utilice en su lugar. La `SerializeRaw` función espera que el objeto de archivo tenga funciones, `Seek`como, que `CSocketFile` no tiene.

Cuando se usa `CArchive` con `CSocketFile` y `CSocket`, es posible que se produzca una `CSocket::Receive` situación en la que se `PumpMessages(FD_READ)`escribe un bucle (by) que espera la cantidad de bytes solicitada. Esto se debe a que Windows Sockets solo permite una llamada recibida por cada notificación `CSocketFile` de `CSocket` FD_READ, pero y permite varias llamadas recibidas por FD_READ. Si obtiene un FD_READ cuando no hay datos para leer, la aplicación se bloquea. Si nunca obtiene otro FD_READ, la aplicación deja de comunicarse a través del socket.

Puede resolver este problema como se indica a continuación. En el `OnReceive` método de la clase Socket, llame `CAsyncSocket::IOCtl(FIONREAD, ...)` a antes de llamar `Serialize` al método de la clase de mensaje cuando los datos esperados que se van a leer del socket superan el tamaño de un paquete TCP (la unidad de transmisión máxima del medio de red , normalmente al menos 1096 bytes). Si el tamaño de los datos disponibles es menor que el necesario, espere a que se reciban todos los datos y, a continuación, inicie la operación de lectura.

En el ejemplo siguiente, `m_dwExpected` es el número aproximado de bytes que el usuario espera recibir. Se supone que se declara en otra parte del código.

[!code-cpp[NVC_MFCSocketThread#4](../../mfc/reference/codesnippet/cpp/csocketfile-class_1.cpp)]

Para obtener más información, vea [Windows Sockets en MFC](../../mfc/windows-sockets-in-mfc.md), [Windows Sockets: Usar sockets con archivos](../../mfc/windows-sockets-using-sockets-with-archives.md), así como la [API de Windows Sockets 2](/windows/win32/WinSock/windows-sockets-start-page-2).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

`CSocketFile`

## <a name="requirements"></a>Requisitos

**Encabezado:** AfxSock. h

##  <a name="csocketfile"></a>  CSocketFile::CSocketFile

Construye un objeto `CSocketFile`.

```
explicit CSocketFile(
    CSocket* pSocket,
    BOOL bArchiveCompatible = TRUE);
```

### <a name="parameters"></a>Parámetros

*pSocket*<br/>
Socket que se va a adjuntar al `CSocketFile` objeto.

*bArchiveCompatible*<br/>
Especifica si el objeto de archivo es para su uso `CArchive` con un objeto. Pase false solo si desea utilizar el `CSocketFile` objeto de forma independiente, como haría con un `CFile` objeto independiente, con ciertas limitaciones. Esta marca cambia el modo `CArchive` `CSocketFile` en que el objeto asociado al objeto administra su búfer para lectura.

### <a name="remarks"></a>Comentarios

El destructor del objeto se desasocia del objeto socket cuando el objeto sale del ámbito o se elimina.

> [!NOTE]
>  También se `CArchive` puede usar como un archivo (limitado) sin un objeto. `CSocketFile` De forma predeterminada, `CSocketFile` el parámetro *bArchiveCompatible* del constructor es true. Esto especifica que el objeto de archivo es para su uso con un archivo. Para usar el objeto de archivo sin un archivo, pase FALSE en el parámetro *bArchiveCompatible* .

En el modo de "compatibilidad de archivo" `CSocketFile` , un objeto proporciona un mejor rendimiento y reduce el riesgo de un "interbloqueo". Un interbloqueo se produce cuando los sockets de envío y recepción están esperando entre sí o para un recurso común. Esta situación puede producirse si `CArchive` el objeto ha funcionado `CSocketFile` con el modo en que lo `CFile` hace con un objeto. Con `CFile`, el archivo puede suponer que si recibe menos bytes de los solicitados, se ha alcanzado el final del archivo.

Con `CSocketFile`, sin embargo, los datos se basan en el mensaje; el búfer puede contener varios mensajes, por lo que recibir menos del número de bytes solicitados no implica el final del archivo. En este caso, la aplicación no se bloquea, como podría `CFile`ocurrir con, y puede seguir leyendo mensajes del búfer hasta que el búfer esté vacío. La función [CArchive:: IsBufferEmpty](../../mfc/reference/carchive-class.md#isbufferempty) es útil para supervisar el estado del búfer del archivo en ese caso.

Para obtener más información sobre el uso `CSocketFile`de, vea los [artículos Windows Sockets: Usar sockets con archivos](../../mfc/windows-sockets-using-sockets-with-archives.md) y [Windows Sockets: Ejemplo de sockets que usan](../../mfc/windows-sockets-example-of-sockets-using-archives.md)archivos.

## <a name="see-also"></a>Vea también

[CFile (clase)](../../mfc/reference/cfile-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CAsyncSocket (clase)](../../mfc/reference/casyncsocket-class.md)<br/>
[CSocket (clase)](../../mfc/reference/csocket-class.md)
