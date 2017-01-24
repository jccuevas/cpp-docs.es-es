---
title: "Windows Sockets: C&#243;mo funcionan los Sockets con archivos | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "sockets [C++], operación sincrónica"
  - "sockets [C++], que contengan archivos"
  - "socket en estado sincrónico"
  - "objeto socket de dos estados"
  - "Windows Sockets [C++], sincrónico"
  - "Windows Sockets [C++], que contengan archivos"
ms.assetid: d8ae4039-391d-44f0-a19b-558817affcbb
caps.latest.revision: 12
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Windows Sockets: C&#243;mo funcionan los Sockets con archivos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este artículo se explica cómo un objeto de [CSocket](../mfc/reference/csocket-class.md) , un objeto de [CSocketFile](../mfc/reference/csocketfile-class.md) , y un objeto de [CArchive](../mfc/reference/carchive-class.md) se combinan para simplificar el envío y recepción de datos a través de un socket de Windows.  
  
 El artículo [Windows Sockets: Ejemplo de utilizar archivos de sockets](../mfc/windows-sockets-example-of-sockets-using-archives.md) muestra la función de **PacketSerialize** .  El objeto de archivo en el ejemplo de **PacketSerialize** funciona como un objeto de archivo pasado a una función de MFC [Serialice](../Topic/CObject::Serialize.md) .  La diferencia esencial es que para los sockets, el archivo se adjunta no a un objeto estándar de [Archivo C](../mfc/reference/cfile-class.md) \(asociado normalmente en un archivo de disco\) pero a un objeto de `CSocketFile` .  En lugar de conectar a un archivo de disco, el objeto de `CSocketFile` conecta con `CSocket` un objeto.  
  
 Un objeto de `CArchive` administra un búfer.  Cuando el búfer de un archivo \(de envío\) que almacena esté completo, un objeto asociado de `CFile` coloca el contenido del búfer de tipo.  Vaciar el búfer de un archivo adjunto a un socket equivale a enviar un mensaje.  Cuando el búfer de un archivo de carga \(receptora\) está lleno, el objeto de `CFile` finaliza la lectura hasta que el búfer vuelve a estar disponible.  
  
 La clase `CSocketFile` deriva de `CFile`, pero no admite funciones de miembro de [Archivo C](../mfc/reference/cfile-class.md) como funciones de posición \(`Seek`, `GetLength`, `SetLength`, etc.\), el bloqueo funciona \(`LockRange`, `UnlockRange`\), o la función de `GetPosition` .  Todos los objetos de [CSocketFile](../mfc/reference/csocketfile-class.md) debe hacer es escribir o leer secuencias de bytes a o del objeto asociado de `CSocket` .  Dado que un archivo no está implicado, las operaciones como `Seek` y `GetPosition` no tienen ningún sentido.  `CSocketFile` se deriva de `CFile`, por lo que heredan normalmente todas estas funciones miembro.  Para evitar esto, las funciones no compatible del miembro de `CFile` se sobrescriben en `CSocketFile` para producir [CNotSupportedException](../mfc/reference/cnotsupportedexception-class.md).  
  
 El objeto de `CSocketFile` llamar a funciones miembro del objeto de `CSocket` para enviar o recibir datos.  
  
 La ilustración siguiente muestra las relaciones entre estos objetos a ambos extremos de la comunicación.  
  
 ![CArchive, CSocketFile y CSocket](../mfc/media/vc38ia1.png "vc38IA1")  
CArchive, CSocketFile y CSocket  
  
 El propósito de esta complejidad manifiesto es de proteger el de la necesidad de administrar los detalles del socket personalmente.  Crea el socket, el archivo, y el archivo, y después inicia enviar o recibir datos insertandolo al archivo o extrayendolo del archivo.  [CArchive](../mfc/reference/carchive-class.md), [CSocketFile](../mfc/reference/csocketfile-class.md), y [CSocket](../mfc/reference/csocket-class.md) administran los detalles en segundo plano.  
  
 Un objeto de `CSocket` es realmente un objeto de la dos\-provincia: a veces asincrónico \(el estado habitual\) y a veces sincrónico.  En su estado asincrónica, un socket puede recibir notificaciones asincrónicas del marco.  Sin embargo, durante una operación como recibir o enviar los datos de socket llega a ser sincrónico.  Esto significa que el socket no recibirá ninguna otra notificación asincrónica hasta que la operación síncrona haya completado.  Dado que intercambia los modos, puede, por ejemplo, hacer algo parecido a:  
  
 [!code-cpp[NVC_MFCSimpleSocket#2](../mfc/codesnippet/CPP/windows-sockets-how-sockets-with-archives-work_1.cpp)]  
  
 Si `CSocket` no se implementó como objeto de la dos\- provincia, es posible recibir las notificaciones adicionales para la misma clase de evento mientras se procesaba una notificación anterior.  Por ejemplo, podría obtener una notificación de `OnReceive` mientras se procesaba `OnReceive`.  En el fragmento de código anterior, extraer `str` de archivo podría provocar la recursividad.  Cambie a estados, `CSocket` evita la recursividad evitando notificaciones adicionales.  La regla general no es ninguna notificación dentro de notificaciones.  
  
> [!NOTE]
>  `CSocketFile` también se puede utilizar como archivo restringido\) de a sin un objeto de `CArchive` .  De forma predeterminada, el parámetro de `bArchiveCompatible` de constructor de `CSocketFile` es **VERDADERO**.  Esto especifica que el objeto de archivo es para el uso con un archivo.  Para utilizar el objeto de archivo sin un archivo, pase **FALSE** en el parámetro de `bArchiveCompatible` .  
  
 En el modo compatible de “archivo”, un objeto de `CSocketFile` proporciona mejor rendimiento y reduce el riesgo de un “interbloqueo.” Un interbloqueo se produce cuando los sockets de envío y que reciben están esperando sí, o esperando un recurso común.  Esta situación puede producirse si el objeto de `CArchive` ejecutó `CSocketFile` la manera que con un objeto de `CFile` .  Con `CFile`, se ha alcanzado el archivo puede suponer que si recibe menos bytes que solicitó, el final del archivo.  Con `CSocketFile`, sin embargo, los datos están mensaje basándose; el búfer puede contener varios mensajes, por lo que recibir menor que el número de bytes solicitados no implica el final del archivo.  La aplicación no bloquea en este caso como podría con `CFile`, y puede continuar leyendo mensajes del búfer hasta que el búfer está vacío.  La función de [IsBufferEmpty](../Topic/CArchive::IsBufferEmpty.md) en `CArchive` es útil para supervisar el estado del búfer del archivo en este caso.  
  
 Para obtener más información, vea [Windows Sockets: Mediante sockets con archivos](../mfc/windows-sockets-using-sockets-with-archives.md)  
  
## Vea también  
 [Windows Sockets en MFC](../mfc/windows-sockets-in-mfc.md)   
 [CObject::Serialize](../Topic/CObject::Serialize.md)