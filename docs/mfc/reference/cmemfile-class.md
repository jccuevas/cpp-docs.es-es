---
title: "CMemFile Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMemFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMemFile class"
  - "memory files"
  - "temporary files, memory files"
ms.assetid: 20e86515-e465-4f73-b2ea-e49789d63165
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CMemFile Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

[Archivo C](../../mfc/reference/cfile-class.md)\- clase derivada que admite archivos de memoria.  
  
## Sintaxis  
  
```  
class CMemFile : public CFile  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMemFile::CMemFile](../Topic/CMemFile::CMemFile.md)|Construye un objeto de archivo de memoria.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMemFile::Attach](../Topic/CMemFile::Attach.md)|Asocia un bloque de memoria a `CMemFile`.|  
|[CMemFile::Detach](../Topic/CMemFile::Detach.md)|Desasocia el bloque de memoria de `CMemFile` y devuelve un puntero al bloque de memoria desasociado.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMemFile::Alloc](../Topic/CMemFile::Alloc.md)|Reemplace para modificar el comportamiento de la asignación de memoria.|  
|[CMemFile::Free](../Topic/CMemFile::Free.md)|Reemplace para modificar el comportamiento de la desasignación de memoria.|  
|[CMemFile::GrowFile](../Topic/CMemFile::GrowFile.md)|Reemplace para modificar el comportamiento al crecer un archivo.|  
|[CMemFile::Memcpy](../Topic/CMemFile::Memcpy.md)|Reemplace para modificar el comportamiento de la copia de memoria al leer y escribir los archivos.|  
|[CMemFile::Realloc](../Topic/CMemFile::Realloc.md)|Reemplace para modificar el comportamiento de reasignación de memoria.|  
  
## Comentarios  
 Estos archivos de memoria se comportan como los archivos de disco salvo que el archivo se almacena en RAM en lugar de en el disco.  Un archivo de memoria es útil para el almacenamiento temporal rápido o para transferir bytes sin formato o objetos serializados entre procesos independientes.  
  
 Los objetos de`CMemFile` automáticamente pueden asignar su propia memoria o adjuntar su propio bloque de memoria al objeto de `CMemFile` llamando a [Asociar](../Topic/CMemFile::Attach.md).  En cualquier caso, la memoria para crecer el archivo automáticamente de la memoria se asigna en `nGrowBytes`\- incrementos ordenados si `nGrowBytes` no es cero.  
  
 El bloque de memoria automáticamente se eliminará sobre la destrucción de objetos `CMemFile` si la memoria se asignó originalmente por el objeto de `CMemFile` ; si no, es responsable de la desasignación de memoria que asoció el objeto.  
  
 Puede tener acceso al bloque de memoria a través del puntero proporcionado cuando se desasocia del objeto de `CMemFile` llamando a [Desasociar](../Topic/CMemFile::Detach.md).  
  
 El uso más común de `CMemFile` es crear un objeto de `CMemFile` y utilizarlo llamando al miembro de [Archivo C](../../mfc/reference/cfile-class.md) funciona.  Observe que crea `CMemFile` automáticamente abre: no llama [CFile::Open](../Topic/CFile::Open.md), que se utiliza para los archivos de disco.  Dado que `CMemFile` no utiliza un archivo de disco, no utilice y no tiene el miembro de datos `CFile::m_hFile` ningún significado.  
  
 Las funciones [duplicado](../Topic/CFile::Duplicate.md), [LockRange](../Topic/CFile::LockRange.md), y [UnlockRange](../Topic/CFile::UnlockRange.md) miembro de `CFile` no se implementan para `CMemFile`.  Si llama a estas funciones en un objeto de `CMemFile` , obtendrá [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).  
  
 `CMemFile` utiliza las funciones de la biblioteca en tiempo de ejecución [malloc](../../c-runtime-library/reference/malloc.md), [realloc](../../c-runtime-library/reference/realloc.md), y [libre](../../c-runtime-library/reference/free.md) para asignar, para reasignar, y para desasignar memoria; y intrínseco [memcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md) para bloquear memoria de copia al leer y escribir.  Si desea cambiar este comportamiento o el comportamiento cuando `CMemFile` crece un archivo, derive su propia clase de `CMemFile` y reemplazar las funciones adecuadas.  
  
 Para obtener más información sobre `CMemFile`, vea los artículos [archivos en MFC](../../mfc/files-in-mfc.md) y [administración de memoria \(MFC\)](../../mfc/memory-management.md) y vea [El control de archivo](../../c-runtime-library/file-handling.md) en *la referencia de la biblioteca en tiempo de ejecución*.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [Archivo C](../../mfc/reference/cfile-class.md)  
  
 `CMemFile`  
  
## Requisitos  
 **encabezado:** afx.h  
  
## Vea también  
 [CFile Class](../../mfc/reference/cfile-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)