---
title: "CSharedFile Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CSharedFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSharedFile class"
  - "memory files"
  - "shared memory files"
ms.assetid: 5d000422-9ede-4318-a8c9-f7412b674f39
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CSharedFile Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

[CMemFile](../../mfc/reference/cmemfile-class.md)\- clase derivada que admite archivos de memoria compartida.  
  
## Sintaxis  
  
```  
class CSharedFile : public CMemFile  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSharedFile::CSharedFile](../Topic/CSharedFile::CSharedFile.md)|Crea un objeto `CSharedFile`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSharedFile::Detach](../Topic/CSharedFile::Detach.md)|Cierre el archivo de memoria compartida y devuelve el identificador del bloque de memoria.|  
|[CSharedFile::SetHandle](../Topic/CSharedFile::SetHandle.md)|Asocia el archivo de memoria compartida a un bloque de memoria.|  
  
## Comentarios  
 Los archivos de memoria se comportan como los archivos de disco salvo que el archivo se almacena en RAM en lugar de en el disco.  Un archivo de memoria es útil para el almacenamiento temporal rápido o para transferir bytes sin formato o objetos serializados entre procesos independientes.  
  
 Los archivos de la memoria compartida difieren de otros archivos de memoria en esa memoria para ellos se asignan a la función de [GlobalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366574) Windows.  La clase de `CSharedFile` almacena datos en un bloque de memoria global asignado \(creado mediante **GlobalAlloc**\), y este bloque de memoria se puede compartir con DDE, el portapapeles, u otras operaciones de transferencia de datos uniforme de OLE\/COM, por ejemplo, utilizando `IDataObject`.  
  
 **GlobalAlloc** devuelve un identificador de `HGLOBAL` en lugar de un puntero a la memoria, como el puntero devuelto por [malloc](../../c-runtime-library/reference/malloc.md).  El identificador de `HGLOBAL` se necesita en algunas aplicaciones.  Por ejemplo, para colocar datos en el portapapeles necesita un identificador de `HGLOBAL` .  
  
 Tenga en cuenta que `CSharedFile` no utiliza archivos asignados desplazarlo, y los datos no se pueden compartir directamente entre los procesos.  
  
 Los objetos de`CSharedFile` automáticamente pueden asignar su propia memoria o adjuntar su propio bloque de memoria al objeto de `CSharedFile` llamando a [CSharedFile::SetHandle](../Topic/CSharedFile::SetHandle.md).  En cualquier caso, la memoria para crecer el archivo automáticamente de la memoria se asigna en `nGrowBytes`\- incrementos ordenados si `nGrowBytes` no es cero.  
  
 Para obtener más información, vea el artículo [archivos en MFC](../../mfc/files-in-mfc.md) y [El control de archivo](../../c-runtime-library/file-handling.md) en *la referencia de la biblioteca en tiempo de ejecución*.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [Archivo C](../../mfc/reference/cfile-class.md)  
  
 [CMemFile](../../mfc/reference/cmemfile-class.md)  
  
 `CSharedFile`  
  
## Requisitos  
 **encabezado:** afxadv.h  
  
## Vea también  
 [CMemFile Class](../../mfc/reference/cmemfile-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CMemFile Class](../../mfc/reference/cmemfile-class.md)   
 [GlobalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366574)   
 [GlobalFree](http://msdn.microsoft.com/library/windows/desktop/aa366579)   
 [GlobalRealloc](http://msdn.microsoft.com/library/windows/desktop/aa366590)