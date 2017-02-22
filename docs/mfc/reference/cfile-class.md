---
title: "CFile Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CArchive class, using with CFile"
  - "CFile class"
  - "archivos [C++], classes for"
ms.assetid: b2eb5757-d499-4e67-b044-dd7d1abaa0f8
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CFile Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La clase base para las clases del archivo de clase de la Microsoft foundation class.  
  
## Sintaxis  
  
```  
class CFile : public CObject  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CFile::CFile](../Topic/CFile::CFile.md)|Construye un objeto de `CFile` de una ruta o un identificador de archivos.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CFile::Abort](../Topic/CFile::Abort.md)|Cerrar un archivo que omite todas las advertencias y errores.|  
|[CFile::Close](../Topic/CFile::Close.md)|Cerrar un archivo y elimine el objeto.|  
|[CFile::Duplicate](../Topic/CFile::Duplicate.md)|construye un objeto duplicado basado en este archivo.|  
|[CFile::Flush](../Topic/CFile::Flush.md)|Vacía los datos todavía se escriba.|  
|[CFile::GetFileName](../Topic/CFile::GetFileName.md)|Recupera el nombre del archivo seleccionado.|  
|[CFile::GetFilePath](../Topic/CFile::GetFilePath.md)|Recupera la ruta de acceso completa del archivo seleccionado.|  
|[CFile::GetFileTitle](../Topic/CFile::GetFileTitle.md)|Recupera el título del archivo seleccionado.|  
|[CFile::GetLength](../Topic/CFile::GetLength.md)|Recupera la longitud del archivo.|  
|[CFile::GetPosition](../Topic/CFile::GetPosition.md)|Recupera el puntero de archivo actual.|  
|[CFile::GetStatus](../Topic/CFile::GetStatus.md)|Recupera el estado del archivo abierto, o en la versión estática, recupera el estado de la función del archivo especificado \(estático, virtual\).|  
|[CFile::LockRange](../Topic/CFile::LockRange.md)|Bloquea un radio de bytes en un archivo.|  
|[CFile::Open](../Topic/CFile::Open.md)|Abra con seguridad un archivo con una opción de la error\-prueba.|  
|[CFile::Read](../Topic/CFile::Read.md)|Lee datos \(inseparados\) de un archivo en la posición del archivo actual.|  
|[CFile::Remove](../Topic/CFile::Remove.md)|elimina el archivo especificado \(función estática\).|  
|[CFile::Rename](../Topic/CFile::Rename.md)|Cambia el nombre del archivo especificado \(función estática\).|  
|[CFile::Seek](../Topic/CFile::Seek.md)|Coloca el puntero de archivo actual.|  
|[CFile::SeekToBegin](../Topic/CFile::SeekToBegin.md)|Coloca el puntero de archivo actual al principio del archivo.|  
|[CFile::SeekToEnd](../Topic/CFile::SeekToEnd.md)|Coloca el puntero de archivo actual al final del archivo.|  
|[CFile::SetFilePath](../Topic/CFile::SetFilePath.md)|Establece la ruta de acceso completa del archivo seleccionado.|  
|[CFile::SetLength](../Topic/CFile::SetLength.md)|Cambia la longitud del archivo.|  
|[CFile::SetStatus](../Topic/CFile::SetStatus.md)|Establece el estado de la función del archivo especificado \(estático, virtual\).|  
|[CFile::UnlockRange](../Topic/CFile::UnlockRange.md)|Desbloquea un radio de bytes en un archivo.|  
|[CFile::Write](../Topic/CFile::Write.md)|Escribe datos \(inseparados\) en un archivo a la posición del archivo actual.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CFile::operator HANDLE](../Topic/CFile::operator%20HANDLE.md)|un identificador a un objeto de `CFile` .|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CFile::hFileNull](../Topic/CFile::hFileNull.md)|determina si el objeto de `CFile` tiene un identificador válido.|  
|[CFile::m\_hFile](../Topic/CFile::m_hFile.md)|Normalmente contiene el identificador de archivo del sistema operativo.|  
  
### Miembros de datos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CFile::m\_pTM](../Topic/CFile::m_pTM.md)|Puntero al objeto de `CAtlTransactionManager` .|  
  
## Comentarios  
 Proporciona directamente servicios inseparados, binarios de entrada y salida de disco, y admite indirectamente archivos de texto y archivos de memoria entre sus clases derivadas.  `CFile` funciona junto con la clase de `CArchive` para admitir la serialización de objetos de clase de la Microsoft foundation class.  
  
 La relación jerárquica entre esta clase y sus clases derivadas permite que el programa funcionan en todos los objetos a través de la interfaz polimórfica de `CFile` .  un archivo de memoria, por ejemplo, se comporta como un archivo de disco.  
  
 Utilice `CFile` y sus clases derivadas para E\/S de uso general de disco.  Utilice `ofstream` u otras clases iostream de Microsoft para el texto con formato enviados a un archivo de disco.  
  
 Normalmente, un archivo de disco se abre automáticamente en la construcción de `CFile` y cerrado en destrucción.  Las funciones miembro estáticas permiten interrogue el estado de un archivo sin abrir el archivo.  
  
 Para obtener más información sobre cómo utilizar `CFile`, vea los artículos [archivos en MFC](../../mfc/files-in-mfc.md) y [El control de archivo](../../c-runtime-library/file-handling.md) en *la referencia de la biblioteca en tiempo de ejecución*.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CFile`  
  
## Requisitos  
 **encabezado:** afx.h  
  
## Vea también  
 [ejemplo DRAWCLI de MFC](../../top/visual-cpp-samples.md)   
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CStdioFile Class](../../mfc/reference/cstdiofile-class.md)   
 [CMemFile Class](../../mfc/reference/cmemfile-class.md)   
 [Cómo se hago: Utilice la clase de CFile?](http://go.microsoft.com/fwlink/?LinkId=128046)