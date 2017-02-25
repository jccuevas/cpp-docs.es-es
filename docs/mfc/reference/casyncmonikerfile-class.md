---
title: "CAsyncMonikerFile Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CAsyncMonikerFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "controles ActiveX [C++], asincrónico"
  - "asynchronous controls [C++]"
  - "CAsyncMonikerFile class"
  - "IMoniker interface, enlace"
  - "monikers [C++], MFC"
  - "controles OLE [C++], asincrónico"
ms.assetid: 17378b66-a49a-4b67-88e3-7756ad26a2fc
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CAsyncMonikerFile Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Proporciona la funcionalidad para el uso de monikeres asincrónicos en los controles ActiveX \(antes controles OLE\).  
  
## Sintaxis  
  
```  
class CAsyncMonikerFile : public CMonikerFile  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAsyncMonikerFile::CAsyncMonikerFile](../Topic/CAsyncMonikerFile::CAsyncMonikerFile.md)|Crea un objeto `CAsyncMonikerFile`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAsyncMonikerFile::Close](../Topic/CAsyncMonikerFile::Close.md)|Cierre y libera todos los recursos.|  
|[CAsyncMonikerFile::GetBinding](../Topic/CAsyncMonikerFile::GetBinding.md)|Recupera un puntero al enlace de descargas asincrónicas.|  
|[CAsyncMonikerFile::GetFormatEtc](../Topic/CAsyncMonikerFile::GetFormatEtc.md)|Recupera el formato de los datos en la secuencia.|  
|[CAsyncMonikerFile::Open](../Topic/CAsyncMonikerFile::Open.md)|Abra un archivo de forma asincrónica.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAsyncMonikerFile::CreateBindStatusCallback](../Topic/CAsyncMonikerFile::CreateBindStatusCallback.md)|Crea un objeto COM que implementa `IBindStatusCallback`.|  
|[CAsyncMonikerFile::GetBindInfo](../Topic/CAsyncMonikerFile::GetBindInfo.md)|Llamado por la biblioteca del sistema OLE para solicitar información en el tipo de enlace que se va a crear.|  
|[CAsyncMonikerFile::GetPriority](../Topic/CAsyncMonikerFile::GetPriority.md)|Llamado por la biblioteca del sistema\) para obtener la prioridad del enlace.|  
|[CAsyncMonikerFile::OnDataAvailable](../Topic/CAsyncMonikerFile::OnDataAvailable.md)|Denominado para proporcionar datos como está disponible al cliente durante operaciones asincrónicas de enlace.|  
|[CAsyncMonikerFile::OnLowResource](../Topic/CAsyncMonikerFile::OnLowResource.md)|Se invoca cuando los recursos son baja.|  
|[CAsyncMonikerFile::OnProgress](../Topic/CAsyncMonikerFile::OnProgress.md)|Denominado para indicar progreso del proceso de transferencia de datos.|  
|[CAsyncMonikerFile::OnStartBinding](../Topic/CAsyncMonikerFile::OnStartBinding.md)|Se llama cuando el enlace es el iniciar hacia arriba.|  
|[CAsyncMonikerFile::OnStopBinding](../Topic/CAsyncMonikerFile::OnStopBinding.md)|Llamado cuando se detiene la descarga asincrónica.|  
  
## Comentarios  
 Derivado de [CMonikerFile](../../mfc/reference/cmonikerfile-class.md), que a su vez se deriva de [COleStreamFile](../../mfc/reference/colestreamfile-class.md), `CAsyncMonikerFile` utiliza la interfaz de [IMoniker](http://msdn.microsoft.com/library/windows/desktop/ms679705) para tener acceso a cualquier secuencia de datos de forma asincrónica, incluidos los archivos de carga de forma asincrónica desde una dirección URL.  Los archivos pueden ser propiedades de datapath de controles ActiveX.  
  
 Los monikeres asincrónicos se utilizan principalmente en aplicaciones habilitadas para Internet y controles ActiveX para proporcionar una interfaz de usuario receptivo durante las transferencias de archivos.  Un ejemplo típico de esto es el uso de [CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md) de proporcionar las propiedades asincrónicas para controles ActiveX.  El objeto de `CDataPathProperty` conseguirá repetidamente una devolución de llamada para indicar la disponibilidad de nuevos datos durante un proceso largo de intercambio de propiedad.  
  
 Para obtener más información sobre cómo utilizar monikeres asincrónicos y controles ActiveX en aplicaciones de internet, vea los artículos siguientes:  
  
-   [Primeros pasos de internet: monikeres asincrónicos](../../mfc/asynchronous-monikers-on-the-internet.md)  
  
-   [Primeros pasos de internet: Controles ActiveX](../../mfc/activex-controls-on-the-internet.md)  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [Archivo C](../../mfc/reference/cfile-class.md)  
  
 [COleStreamFile](../../mfc/reference/colestreamfile-class.md)  
  
 [CMonikerFile](../../mfc/reference/cmonikerfile-class.md)  
  
 `CAsyncMonikerFile`  
  
## Requisitos  
 **encabezado:** afxole.h  
  
## Vea también  
 [CMonikerFile Class](../../mfc/reference/cmonikerfile-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CMonikerFile Class](../../mfc/reference/cmonikerfile-class.md)   
 [CDataPathProperty Class](../../mfc/reference/cdatapathproperty-class.md)   
 [Asynchronous Versus Synchronous Monikers](http://msdn.microsoft.com/library/windows/desktop/ms687193)