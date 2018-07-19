---
title: 'Windows Sockets: Cómo funcionan los Sockets con archivos de almacenamiento | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Windows Sockets [MFC], synchronous
- sockets [MFC], synchronous operation
- sockets [MFC], with archives
- synchronous state socket
- Windows Sockets [MFC], with archives
- two-state socket object
ms.assetid: d8ae4039-391d-44f0-a19b-558817affcbb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6c4f581acb0af27f44c88d59597e52b057991ee4
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/26/2018
ms.locfileid: "36954284"
---
# <a name="windows-sockets-how-sockets-with-archives-work"></a>Windows Sockets: Cómo funcionan los Sockets con archivos
Este artículo se explica cómo un [CSocket](../mfc/reference/csocket-class.md) objeto, un [CSocketFile](../mfc/reference/csocketfile-class.md) objeto y un [CArchive](../mfc/reference/carchive-class.md) objeto se combinan para simplificar enviar y recibir datos a través de una ventana Espera del socket.  
  
 El artículo [Windows Sockets: ejemplo de Sockets con archivos](../mfc/windows-sockets-example-of-sockets-using-archives.md) presenta el `PacketSerialize` función. El objeto de archivo en el `PacketSerialize` ejemplo funciona como un objeto de archivo pasado a un MFC [Serialize](../mfc/reference/cobject-class.md#serialize) función. La diferencia fundamental es que para los sockets, el archivo no está asociado a un estándar [CFile](../mfc/reference/cfile-class.md) objeto (normalmente asociado a un archivo de disco) sino en un `CSocketFile` objeto. En lugar de conectarse a un archivo de disco, el `CSocketFile` objeto se conecta a un `CSocket` objeto.  
  
 Un `CArchive` objeto administra un búfer. Cuando el búfer de un archivo de almacenamiento (envío) esté completo, un asociado `CFile` objeto escribe el contenido del búfer. Vaciar el búfer de un archivo adjunto a un socket equivale a enviar un mensaje. Cuando el búfer de un archivo de carga (recepción) está lleno, la `CFile` objeto deja de lectura hasta que el búfer esté disponible de nuevo.  
  
 Clase `CSocketFile` deriva de `CFile`, pero no admite [CFile](../mfc/reference/cfile-class.md) funciones miembro como las funciones de posición (`Seek`, `GetLength`, `SetLength`, etc.), el bloqueo de las funciones () `LockRange`, `UnlockRange`), o la `GetPosition` función. Todos los [CSocketFile](../mfc/reference/csocketfile-class.md) objeto debe hacer es escribir o leer secuencias de bytes a o desde el asociado `CSocket` objeto. Porque no está implicado un archivo, las operaciones como `Seek` y `GetPosition` no tienen sentido. `CSocketFile` se deriva de `CFile`, por lo que normalmente se heredan todas estas funciones de miembro. Para evitar este problema, no admitida `CFile` en el que se reemplazan las funciones miembro `CSocketFile` para producir un [CNotSupportedException](../mfc/reference/cnotsupportedexception-class.md).  
  
 El `CSocketFile` objeto llama a funciones de miembro su `CSocket` objeto para enviar o recibir datos.  
  
 La siguiente ilustración muestra las relaciones entre estos objetos en ambos lados de la comunicación.  
  
 ![CArchive, CSocketFile y CSocket](../mfc/media/vc38ia1.gif "vc38ia1")  
CArchive, CSocketFile y CSocket  
  
 El propósito de esta complejidad aparente es evitan la necesidad de administrar los detalles del socket usted mismo. Crear el socket, el archivo y el archivo y, a continuación, empezar a enviar o recibir datos insertando en el archivo de almacenamiento o extraer del archivo. [CArchive](../mfc/reference/carchive-class.md), [CSocketFile](../mfc/reference/csocketfile-class.md), y [CSocket](../mfc/reference/csocket-class.md) administrar los detalles en segundo plano.  
  
 A `CSocket` es realmente un objeto de dos estados: a veces es asincrónico (el estado habitual) y a veces sincrónico. En su estado asincrónico, un socket puede recibir notificaciones asincrónicas desde el marco de trabajo. Sin embargo, durante una operación como la recepción o envío de datos el socket pasa a estado sincrónico. Esto significa que el socket recibirá notificaciones asincrónicas ninguna otra hasta que haya completado la operación sincrónica. Porque cambia el modo, por ejemplo, puede hacer algo parecido a lo siguiente:  
  
 [!code-cpp[NVC_MFCSimpleSocket#2](../mfc/codesnippet/cpp/windows-sockets-how-sockets-with-archives-work_1.cpp)]  
  
 Si `CSocket` no se han implementado como un objeto de dos Estados, es posible recibir notificaciones adicionales para el mismo tipo de evento mientras se procesa una notificación anterior. Por ejemplo, podría obtener un `OnReceive` notificación mientras se procesaba un `OnReceive`. En el fragmento de código anterior, extraer `str` desde el archivo podría provocar la recursividad. Al cambiar estados, `CSocket` evita la recursividad impidiendo las notificaciones adicionales. La regla general es no recibir notificaciones dentro de las notificaciones.  
  
> [!NOTE]
>  A `CSocketFile` también puede usarse como un archivo (limitado) sin un `CArchive` objeto. De forma predeterminada, el `CSocketFile` del constructor *bArchiveCompatible* parámetro es **TRUE**. Esto especifica que el objeto de archivo es para su uso con un archivo. Para usar el objeto de archivo sin un archivo, pase **FALSE** en el *bArchiveCompatible* parámetro.  
  
 En el modo "compatible con el archivo", un `CSocketFile` objeto proporciona un mejor rendimiento y reduce el riesgo de un "interbloqueo". Un interbloqueo se produce cuando los sockets envío y recepción están esperando mutuamente o esperando un recurso común. Esto puede suceder si el `CArchive` objeto ha trabajado con la `CSocketFile` el modo en que lo hace con un `CFile` objeto. Con `CFile`, el archivo puede suponer que si recibe menos bytes que los solicitados, se ha alcanzado el final del archivo. Con `CSocketFile`, sin embargo, están de datos basado en mensajes; el búfer puede contener varios mensajes, por lo que recibir menor que el número de bytes solicitado no implica el final del archivo. La aplicación no se bloquea en este caso, como podría ocurrir con `CFile`, y puede seguir leyendo mensajes del búfer hasta que el búfer está vacío. El [IsBufferEmpty](../mfc/reference/carchive-class.md#isbufferempty) funcionando en `CArchive` es útil para supervisar el estado del búfer del archivo en este caso.  
  
 Para obtener más información, vea [Windows Sockets: usar Sockets con archivos](../mfc/windows-sockets-using-sockets-with-archives.md)  
  
## <a name="see-also"></a>Vea también  
 [Windows Sockets en MFC](../mfc/windows-sockets-in-mfc.md)   
 [CObject:: Serialize](../mfc/reference/cobject-class.md#serialize)

