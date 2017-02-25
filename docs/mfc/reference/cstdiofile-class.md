---
title: "CStdioFile Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CStdioFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CStdioFile class"
  - "I/O [MFC], stream"
  - "stream I/O"
ms.assetid: 88c2274c-4f0e-4327-882a-557ba4b3ae15
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CStdioFile Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Representa el archivo de la secuencia en tiempo de ejecución de C. como se abierto por la función [fopen](../../c-runtime-library/reference/fopen-wfopen.md)en tiempo de ejecución.  
  
## Sintaxis  
  
```  
class CStdioFile : public CFile  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CStdioFile::CStdioFile](../Topic/CStdioFile::CStdioFile.md)|Construye un objeto de `CStdioFile` de una ruta o un puntero de archivo.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CStdioFile::Open](../Topic/CStdioFile::Open.md)|Sobrecargado.  Open se ha diseñado para el constructor predeterminado de `CStdioFile` \(reemplaza [Archivo ctype:: Abrir](../Topic/CFile::Open.md)\).|  
|[CStdioFile::ReadString](../Topic/CStdioFile::ReadString.md)|Lee una línea de texto única.|  
|[CStdioFile::Seek](../Topic/CStdioFile::Seek.md)|Coloca el puntero de archivo actual.|  
|[CStdioFile::WriteString](../Topic/CStdioFile::WriteString.md)|Escribe una línea de texto única.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CStdioFile::m\_pStream](../Topic/CStdioFile::m_pStream.md)|contiene un puntero a un archivo abierto.|  
  
## Comentarios  
 Los archivos de la secuencia se almacenan en búfer y se pueden abrir en el modo de texto \(valor predeterminado\) o el modo binario.  
  
 El modo de texto proporciona el procesamiento especial para los pares de retorno\-avance de línea de carro.  Cuando se escribe un carácter de nueva línea \(0x0A\) a un objeto de `CStdioFile` del modo de texto, el par de byte \(0x0D, 0x0A\) se envía al archivo.  Cuando se leen, el par de byte \(0x0D, 0x0A\) se convierte en un solo byte 0x0A.  
  
 [Archivo C](../../mfc/reference/cfile-class.md) funciona [duplicado](../Topic/CFile::Duplicate.md), [LockRange](../Topic/CFile::LockRange.md), y [UnlockRange](../Topic/CFile::UnlockRange.md) no se admite para `CStdioFile`.  
  
 Si llama a estas funciones en `CStdioFile`, obtendrá [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).  
  
 Para obtener más información sobre cómo utilizar `CStdioFile`, vea los artículos [archivos en MFC](../../mfc/files-in-mfc.md) y [El control de archivo](../../c-runtime-library/file-handling.md) en *la referencia de la biblioteca en tiempo de ejecución*.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [Archivo C](../../mfc/reference/cfile-class.md)  
  
 `CStdioFile`  
  
## Requisitos  
 **encabezado:** afx.h  
  
## Vea también  
 [CFile Class](../../mfc/reference/cfile-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CFile Class](../../mfc/reference/cfile-class.md)   
 [CFile::Duplicate](../Topic/CFile::Duplicate.md)   
 [CFile::LockRange](../Topic/CFile::LockRange.md)   
 [CFile::UnlockRange](../Topic/CFile::UnlockRange.md)   
 [CNotSupportedException Class](../../mfc/reference/cnotsupportedexception-class.md)   
 [Cómo se hago: Utilice la clase de CFile?](http://go.microsoft.com/fwlink/?LinkId=128046)