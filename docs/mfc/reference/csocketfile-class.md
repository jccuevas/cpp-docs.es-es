---
title: "CSocketFile Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CSocketFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "archives [C++], red"
  - "CSocketFile class"
  - "networks [C++], archive"
  - "networks [C++], serializing to"
  - "serialización [C++], red"
  - "SOCKET handle"
ms.assetid: 7924c098-5f72-40d6-989d-42800a47958f
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# CSocketFile Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Un objeto de `CFile` utilizado para enviar y recibir datos a través de una red mediante el Windows Sockets.  
  
## Sintaxis  
  
```  
class CSocketFile : public CFile  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSocketFile::CSocketFile](../Topic/CSocketFile::CSocketFile.md)|Crea un objeto `CSocketFile`.|  
  
## Comentarios  
 Puede adjuntar el objeto de `CSocketFile` a un objeto de `CSocket` con este fin.  También puede, y normalmente hace, asocia el objeto de `CSocketFile` a un objeto de `CArchive` para simplificar el envío y recepción de datos mediante la serialización de MFC.  
  
 Para serializar \(enviar\) datos, insértela en el archivo, que llama a funciones miembro de `CSocketFile` para escribir datos en el objeto de `CSocket` .  Para deserializar \(recibir\) datos, se extrae del archivo.  Esto hace que el archivo para llamar a funciones miembro de `CSocketFile` para leer datos del objeto de `CSocket` .  
  
> [!TIP]
>  Además de utilizar `CSocketFile` como se describe aquí, puede utilizarlo como objeto independiente del archivo, igual que las de `CFile`, la clase base.  También puede utilizar `CSocketFile` con cualquier función archivo\-basada de serialización de MFC.  Dado que `CSocketFile` no admite toda la funcionalidad de los entity\_CFile, algún valor predeterminado MFC serializa funciones no es compatible con `CSocketFile`.  Esto es especialmente cierto de la clase de `CEditView` .  No debe intentar serializar los datos de `CEditView` a través de un objeto de `CArchive` asociado a un objeto de `CSocketFile` mediante `CEditView::SerializeRaw`; uso **CEditView:: serialice** en su lugar.  La función de `SerializeRaw` espera que el objeto de archivo tiene funciones, como `Seek`, que `CSocketFile` no tiene.  
  
 Cuando se utiliza `CArchive` con `CSocketFile` y `CSocket`, es posible que encuentre un escenario donde **CSocket::Recibir** escribe un bucle \(por **PumpMessages \(FD\_READ\)**\) que espera la cantidad solicitado de bytes.  Esto es porque el Windows Sockets sólo permite una llamada de recv por la notificación de FD\_READ, pero `CSocketFile` y `CSocket` permiten varias llamadas de recv por FD\_READ.  Si obtiene un FD\_READ cuando no hay datos para leer, la aplicación no responder.  Si no obtiene otro FD\_READ, la aplicación detiene la comunicación sobre el socket.  
  
 Puede resolver este problema como sigue.  En el método de `OnReceive` de la clase de socket, llamada **CAsyncSocket:: IOCtl \(FIONREAD,…\)** antes de llamar al método de `Serialize` de la clase de mensaje cuando los datos esperado que se leerá de socket supera el tamaño de un paquete TCP \(máximo Transmission Unit medio de red, normalmente por lo menos de 1096 bytes\).  Si el tamaño de los datos disponibles menos que se necesita, espere todos los datos que se van a recibir y inicie sólo la operación de lectura.  
  
 En el ejemplo siguiente, `m_dwExpected` es el número de bytes aproximado que el usuario espera recibir.  Se supone que lo declara en otra parte del código.  
  
 [!code-cpp[NVC_MFCSocketThread#4](../../mfc/reference/codesnippet/CPP/csocketfile-class_1.cpp)]  
  
 Para obtener más información, vea [Windows Sockets en MFC](../../mfc/windows-sockets-in-mfc.md), [Windows Sockets: Mediante sockets con archivos](../../mfc/windows-sockets-using-sockets-with-archives.md), así como [Windows Sockets 2 API](http://msdn.microsoft.com/library/windows/desktop/ms740673).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [Archivo C](../../mfc/reference/cfile-class.md)  
  
 `CSocketFile`  
  
## Requisitos  
 **encabezado:** afxsock.h  
  
## Vea también  
 [CFile Class](../../mfc/reference/cfile-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CAsyncSocket Class](../../mfc/reference/casyncsocket-class.md)   
 [CSocket Class](../../mfc/reference/csocket-class.md)