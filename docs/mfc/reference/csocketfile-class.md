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
ms.openlocfilehash: 83810a05925e5c8302240b61d95c131fdd78b426
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318168"
---
# <a name="csocketfile-class"></a>CSocketFile (clase)

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

## <a name="remarks"></a>Observaciones

Puede asociar `CSocketFile` el objeto `CSocket` a un objeto para este propósito. También puede, y normalmente `CSocketFile` lo hace, adjuntar el objeto a un `CArchive` objeto para simplificar el envío y la recepción de datos mediante la serialización MFC.

Para serializar (enviar) datos, insértelos en el archivo, que llama a funciones `CSocketFile` miembro para escribir datos en el `CSocket` objeto. Para deserializar (recibir) datos, extraiga del archivo. Esto hace que `CSocketFile` el archivo llame a `CSocket` funciones miembro para leer datos del objeto.

> [!TIP]
> Además `CSocketFile` de usar como se describe aquí, puede usarlo como un `CFile`objeto de archivo independiente, al igual que puede con , su clase base. También puede `CSocketFile` usar con cualquier función de serialización MFC basada en archivado. Dado `CSocketFile` que no `CFile`admite toda la funcionalidad de 's, `CSocketFile`algunas funciones de serialización MFC predeterminadas no son compatibles con . Esto es particularmente `CEditView` cierto en la clase. No debe intentar `CEditView` serializar `CArchive` datos a `CSocketFile` través `CEditView::SerializeRaw`de un objeto asociado a un objeto mediante ; usar `CEditView::Serialize` en su lugar. La `SerializeRaw` función espera que el objeto `Seek`de `CSocketFile` archivo tenga funciones, como , que no tiene.

Cuando usted `CArchive` `CSocketFile` utiliza `CSocket`con y , `CSocket::Receive` usted puede ser `PumpMessages(FD_READ)`que encuentre una situación donde entra un loop (por ) esperando la cantidad solicitada de bytes. Esto se debe a que los sockets de `CSocketFile` Windows `CSocket` solo permiten una llamada recv por notificación FD_READ, pero y permiten varias llamadas recv por FD_READ. Si obtiene una FD_READ cuando no hay datos que leer, la aplicación se bloquea. Si nunca obtiene otro FD_READ, la aplicación deja de comunicarse a través del socket.

Puede resolver este problema de la siguiente manera. En `OnReceive` el método de la `CAsyncSocket::IOCtl(FIONREAD, ...)` clase de `Serialize` socket, llame antes de llamar al método de la clase de mensaje cuando los datos esperados que se leerán desde el socket superan el tamaño de un paquete TCP (unidad de transmisión máxima del medio de red, normalmente al menos 1096 bytes). Si el tamaño de los datos disponibles es menor que el necesario, espere a que se reciban todos los datos y, a continuación, inicie la operación de lectura.

En el ejemplo `m_dwExpected` siguiente, es el número aproximado de bytes que el usuario espera recibir. Se supone que se declara en otra parte del código.

[!code-cpp[NVC_MFCSocketThread#4](../../mfc/reference/codesnippet/cpp/csocketfile-class_1.cpp)]

Para obtener más información, vea [Windows Sockets en MFC](../../mfc/windows-sockets-in-mfc.md), Windows [Sockets: Using Sockets with Archives](../../mfc/windows-sockets-using-sockets-with-archives.md), así como [Windows Sockets 2 API](/windows/win32/WinSock/windows-sockets-start-page-2).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

`CSocketFile`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxsock.h

## <a name="csocketfilecsocketfile"></a><a name="csocketfile"></a>CSocketFile::CSocketFile

Construye un objeto `CSocketFile`.

```
explicit CSocketFile(
    CSocket* pSocket,
    BOOL bArchiveCompatible = TRUE);
```

### <a name="parameters"></a>Parámetros

*pSocket*<br/>
El socket que `CSocketFile` se va a adjuntar al objeto.

*bArchiveCompatible*<br/>
Especifica si el objeto de archivo `CArchive` se utiliza con un objeto. Pase FALSE solo si desea `CSocketFile` utilizar el objeto de forma independiente como `CFile` lo haría con un objeto independiente, con ciertas limitaciones. Esta marca cambia `CArchive` la forma `CSocketFile` en que el objeto asociado al objeto administra su búfer para su lectura.

### <a name="remarks"></a>Observaciones

El destructor del objeto se desasocia del objeto de socket cuando el objeto sale del ámbito o se elimina.

> [!NOTE]
> A `CSocketFile` también se puede utilizar como un `CArchive` archivo (limitado) sin un objeto. De forma `CSocketFile` predeterminada, el parámetro *bArchiveCompatible* del constructor es TRUE. Esto especifica que el objeto de archivo se utiliza con un archivo. Para utilizar el objeto de archivo sin un archivo, pase FALSE en el *bArchiveCompatible* parámetro.

En su modo "compatible `CSocketFile` con archivos", un objeto proporciona un mejor rendimiento y reduce el peligro de un "interbloqueo". Un interbloqueo se produce cuando los sockets de envío y recepción están esperando entre sí, o para un recurso común. Esta situación puede `CArchive` producirse `CSocketFile` si el objeto `CFile` trabaja con la forma en que lo hace con un objeto. Con `CFile`, el archivo puede suponer que si recibe menos bytes de los que solicitó, se ha alcanzado el final del archivo.

Sin embargo, con `CSocketFile`, los datos se basan en mensajes; el búfer puede contener varios mensajes, por lo que recibir menos del número de bytes solicitados no implica el final del archivo. La aplicación no se bloquea en `CFile`este caso como podría con , y puede seguir leyendo mensajes desde el búfer hasta que el búfer está vacío. La función [CArchive::IsBufferEmpty](../../mfc/reference/carchive-class.md#isbufferempty) es útil para supervisar el estado del búfer del archivo en tal caso.

Para obtener más información `CSocketFile`sobre el uso de , vea los artículos [Windows Sockets: Using Sockets with Archives](../../mfc/windows-sockets-using-sockets-with-archives.md) and [Windows Sockets: Example of Sockets Using Archives](../../mfc/windows-sockets-example-of-sockets-using-archives.md).

## <a name="see-also"></a>Consulte también

[CFile (clase)](../../mfc/reference/cfile-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CAsyncSocket (clase)](../../mfc/reference/casyncsocket-class.md)<br/>
[CSocket (clase)](../../mfc/reference/csocket-class.md)
