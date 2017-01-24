---
title: "Windows Sockets: Orden de bytes | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "problemas de orden de byte en programación de sockets"
  - "sockets [C++], problemas de orden de byte"
  - "Windows Sockets [C++], problemas de orden de byte"
ms.assetid: 8a787a65-f9f4-4002-a02f-ac25a5dace5d
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Windows Sockets: Orden de bytes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Este artículo y dos casos de acompañan explican varios aspectos de la programación de Windows Sockets.  Este artículo trata el orden de bytes.  Los demás problemas se cubren en los casos: [Windows Sockets: Bloquear](../mfc/windows-sockets-blocking.md) y [Windows Sockets: Convertir cadenas](../mfc/windows-sockets-converting-strings.md).  
  
 Si usa o deriva de la clase [CAsyncSocket](../mfc/reference/casyncsocket-class.md), deberá administrar estos problemas personalmente.  Si usa o deriva de la clase [CSocket](../mfc/reference/csocket-class.md), MFC los administra.  
  
## El orden de byte  
 Diferentes arquitecturas de equipo almacenan a veces datos mediante varios pedidos de byte.  Por ejemplo, los equipos Intel\- basados almacenan datos en el orden inverso de equipos Macintosh \(Motorola\).  El orden de bytes Intel, denominado “pequeño \- Endian”, es también el inverso orden estándar de red “grande \- Endian”.  La tabla siguiente se explican estos términos.  
  
### El grande y pequeño \- Endian orden de byte  
  
|El orden de byte|Significado|  
|----------------------|-----------------|  
|Grande\-Endian|El byte más significativo se encuentra en el extremo izquierdo de una palabra.|  
|Pequeño\-Endian|El byte más significativo se encuentra en el extremo derecho de una palabra.|  
  
 Normalmente, no tiene que preocuparse de la conversión de orden de bytes para los datos que envía y recibe a través de la red, pero hay situaciones en las que debe convertir pedidos de byte.  
  
## Cuando debe convertir pedidos de byte  
 Debe convertir pedidos de byte en las situaciones siguientes:  
  
-   Pasa la información que necesita interpretar por la red, en comparación con los datos que está enviando a otro equipo.  Por ejemplo, podría pasar los puertos y las direcciones, que la red debe entender.  
  
-   La aplicación de servidor a la que está comunicando no es una aplicación MFC \(y no tenga código fuente para él\).  Este método llama para las conversiones de orden de bytes si los dos equipos no comparten mismo orden de byte.  
  
## Cuando no se tiene que convertir pedidos de byte  
 Puede evitar el trabajo de convertir pedidos de byte en las situaciones siguientes:  
  
-   Los equipos en ambos extremos pueden acordar no cambiar bytes, y ambos equipos utilizan el mismo orden de bytes.  
  
-   El servidor que se está comunicando con es una aplicación MFC.  
  
-   Tiene código fuente del servidor que se está comunicando con, de modo que puede indicar explícitamente si debe convertir pedidos de byte o no.  
  
-   Puede trasladar el servidor a MFC.  Esto es fácil de hacer, y el resultado es normalmente un código más pequeño, más rápido.  
  
 Trabajar con [CAsyncSocket](../mfc/reference/casyncsocket-class.md), debe administrar cualquier conversión necesaria de orden de bytes personalmente.  El Windows Sockets estandariza “grande \- Endian” modelo de orden de bytes y proporciona funciones convertir entre este orden y otros.  [CArchive](../mfc/reference/carchive-class.md), sin embargo, que se utiliza con [CSocket](../mfc/reference/csocket-class.md), utiliza \(“pequeño \- Endian”\) haber ordenado opuesto, pero `CArchive` se ocupa de los detalles de las conversiones de orden de bytes para usted.  Mediante este estándar de ordenación en las aplicaciones, o mediante las funciones de conversión de orden de bytes de Windows Sockets, puede hacer que el código sea más portátil.  
  
 El caso ideal para utilizar sockets de MFC es cuando se escribe en ambos extremos de la comunicación y se usa MFC en ambos extremos.  Si escribe una aplicación que comunicará con aplicaciones de no de MFC, como un servidor FTP, probablemente necesitará administrar byte\- intercambiarse antes de que pase datos al objeto de archivo, usando las rutinas de conversión de Windows Sockets **ntohs**, **ntohl**, **htons**, y **htonl**.  Un ejemplo de estas funciones utilizado en comunicarse con una aplicación de MFC que aparece más adelante en este artículo.  
  
> [!NOTE]
>  Cuando el otro extremo de la comunicación no es una aplicación MFC, también debe evitar fluir objetos de C\+\+ derivados de `CObject` en el archivo porque el receptor no podrá controlarlos.  Vea la nota en [Windows Sockets: Mediante sockets con archivos](../mfc/windows-sockets-using-sockets-with-archives.md).  
  
 Para obtener más información sobre pedidos de byte, vea la especificación de Windows Sockets, disponible en [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)].  
  
## Un ejemplo de conversión de orden de bytes  
 El ejemplo siguiente se muestra una función de serialización para un objeto de `CSocket` que utilice un archivo.  También muestra el uso de las funciones de conversión de orden de bytes en Windows Sockets API.  
  
 Este ejemplo muestra un escenario en el que está programando un cliente que se comunique con una aplicación de servidor de que MFC para la que no tenga acceso al código fuente.  En este escenario, debe suponer que el servidor de que MFC utiliza orden de bytes estándar de la red.  En cambio, la aplicación cliente de MFC utiliza un objeto de `CArchive` con un objeto de `CSocket` , y `CArchive` utiliza “pequeño \- Endian” orden de bytes, el cambio del estándar de la red.  
  
 Suponga que el servidor de no MFC que piensa comunicarse tiene un protocolo establecido para un paquete de mensaje como el siguiente:  
  
 [!code-cpp[NVC_MFCSimpleSocket#5](../mfc/codesnippet/CPP/windows-sockets-byte-ordering_1.cpp)]  
  
 En términos de MFC, esto sería expresada como sigue:  
  
 [!code-cpp[NVC_MFCSimpleSocket#6](../mfc/codesnippet/CPP/windows-sockets-byte-ordering_2.cpp)]  
  
 En C\+\+, `struct` es esencialmente la misma operación que una clase.  La estructura de `Message` puede tener funciones miembro, como la función miembro de `Serialize` declarada anteriormente.  La función miembro de `Serialize` sería similar a:  
  
 [!code-cpp[NVC_MFCSimpleSocket#7](../mfc/codesnippet/CPP/windows-sockets-byte-ordering_3.cpp)]  
  
 Llamadas de este ejemplo para las conversiones de orden de bytes de datos porque hay una falta de correspondencia clara entre orden de byte de la aplicación de servidor de que MFC en un extremo y `CArchive` utilizado en la aplicación cliente de MFC en el otro extremo.  El ejemplo muestra algunas de las funciones de conversión de orden de bytes esas fuentes de Windows Sockets.  La tabla siguiente se describen estas funciones.  
  
### Funciones de conversión de orden de bytes de Windows Sockets  
  
|Función|Objetivo|  
|-------------|--------------|  
|**ntohs**|Convierte una cantidad de 16 bits de orden de bytes de red al orden de bytes host \(grande \- Endian a pequeño \- Endian\).|  
|**ntohl**|Convierte una cantidad de 32 bits de orden de bytes de red al orden de bytes host \(grande \- Endian a pequeño \- Endian\).|  
|**Htons**|Convierte una cantidad de 16 bits de orden de bytes del host al orden de bytes de red \(pequeño \- Endian a grande \- Endian\).|  
|**Htonl**|Convierte una cantidad de 32 bits de orden de bytes del host al orden de bytes de red \(pequeño \- Endian a grande \- Endian\).|  
  
 Otro punto de este ejemplo es que cuando la aplicación de socket en el otro extremo de la comunicación es una aplicación de que MFC, debe evitar hacer algo parecido a:  
  
 `ar << pMsg;`  
  
 donde es puntero `pMsg` al objeto en cuestión. derivado de la clase `CObject`.  Esto enviará información de MFC extensor asociada a los objetos y el servidor no la entenderá, como si fuera una aplicación MFC.  
  
 Para obtener más información, vea:  
  
-   [Windows Sockets: Usar la clase CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)  
  
-   [Windows Sockets: En segundo plano](../mfc/windows-sockets-background.md)  
  
-   [Windows Sockets: Sockets de secuencia](../mfc/windows-sockets-stream-sockets.md)  
  
-   [Windows Sockets: Sockets de datagrama](../mfc/windows-sockets-datagram-sockets.md)  
  
## Vea también  
 [Windows Sockets en MFC](../mfc/windows-sockets-in-mfc.md)