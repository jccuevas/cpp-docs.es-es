---
title: Clase CSharedFile | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CSharedFile
- AFXADV/CSharedFile
- AFXADV/CSharedFile::CSharedFile
- AFXADV/CSharedFile::Detach
- AFXADV/CSharedFile::SetHandle
dev_langs:
- C++
helpviewer_keywords:
- CSharedFile [MFC], CSharedFile
- CSharedFile [MFC], Detach
- CSharedFile [MFC], SetHandle
ms.assetid: 5d000422-9ede-4318-a8c9-f7412b674f39
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: df3c052f3cefb3aa7d2a55e81fd5f7813632ceb1
ms.sourcegitcommit: be0e3457f2884551f18e183ef0ea65c3ded7f689
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/28/2018
ms.locfileid: "37078288"
---
# <a name="csharedfile-class"></a>Clase CSharedFile
El [CMemFile](../../mfc/reference/cmemfile-class.md)-clase derivada que es compatible con archivos de memoria compartida.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CSharedFile : public CMemFile  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSharedFile::CSharedFile](#csharedfile)|Construye un objeto `CSharedFile`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSharedFile::Detach](#detach)|Cierra el archivo de memoria compartida y devuelve el identificador de su bloque de memoria.|  
|[CSharedFile::SetHandle](#sethandle)|Adjunta el archivo de memoria compartida para un bloque de memoria.|  
  
## <a name="remarks"></a>Comentarios  
 Archivos de memoria se comportan como los archivos de disco salvo que el archivo se almacena en la memoria RAM en lugar de en disco. Un archivo de memoria es útil para el almacenamiento temporal rápido o para la transferencia de bytes sin formato u objetos serializados entre procesos independientes.  
  
 Archivos de memoria compartida difieren de otros archivos de memoria en que se asigna memoria para ellos con el [GlobalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366574) la función de Windows. El `CSharedFile` clase almacena los datos en un bloque de memoria asignado globalmente (creado con `GlobalAlloc`), y este bloque de memoria se puede compartir con DDE, el Portapapeles u otros OLE/COM datos uniforme operaciones de transferencia, por ejemplo, mediante `IDataObject`.  
  
 `GlobalAlloc` Devuelve un `HGLOBAL` controlar en lugar de un puntero a la memoria, como el puntero devuelto por [malloc](../../c-runtime-library/reference/malloc.md). El `HGLOBAL` identificador es necesaria en ciertas aplicaciones. Por ejemplo, para colocar datos en el Portapapeles necesita un `HGLOBAL` controlar.  
  
 Tenga en cuenta que `CSharedFile` no asignado a la memoria de uso de archivos y los datos no se puede compartir directamente entre los procesos.  
  
 `CSharedFile` objetos pueden asignar automáticamente su propia memoria o bien puede asociar su propio bloque de memoria a la `CSharedFile` objeto mediante una llamada a [CSharedFile::SetHandle](#sethandle). En cualquier caso, se asigna memoria para aumentar automáticamente el archivo de memoria en `nGrowBytes`-tamaño incrementos si `nGrowBytes` no es cero.  
  
 Para obtener más información, vea el artículo [archivos en MFC](../../mfc/files-in-mfc.md) y [archivo control](../../c-runtime-library/file-handling.md) en el *referencia de la biblioteca de tiempo de ejecución*.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 [CMemFile](../../mfc/reference/cmemfile-class.md)  
  
 `CSharedFile`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxadv.h  
  
##  <a name="csharedfile"></a>  CSharedFile::CSharedFile  
 Construye un `CSharedFile` de objetos y le asigna memoria.  
  
```  
CSharedFile(
    UINT nAllocFlags = GMEM_DDESHARE | GMEM_MOVEABLE,  
    UINT nGrowBytes = 4096);
```  
  
### <a name="parameters"></a>Parámetros  
 *nAllocFlags*  
 Marcas que indica cómo se puede asignar memoria. Vea [GlobalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366574) para obtener una lista de valores de indicador válidos.  
  
 *nGrowBytes*  
 El incremento de la asignación de memoria en bytes.  
  
##  <a name="detach"></a>  CSharedFile::Detach  
 Llame a esta función para cerrar el archivo de memoria y desconectar desde el bloque de memoria.  
  
```  
HGLOBAL Detach();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador del bloque de memoria que contiene el contenido del archivo de memoria.  
  
### <a name="remarks"></a>Comentarios  
 Puede volver a abrirlo mediante una llamada a [SetHandle](#sethandle), utilizando el identificador devuelto por **separar**.  
  
##  <a name="sethandle"></a>  CSharedFile::SetHandle  
 Llame a esta función para adjuntar un bloque de memoria global para la `CSharedFile` objeto.  
  
```  
void SetHandle(
    HGLOBAL hGlobalMemory,  
    BOOL bAllowGrow = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 *hGlobalMemory*  
 Identificador de la memoria global para adjuntarlo a la `CSharedFile`.  
  
 *bAllowGrow*  
 Especifica si el bloque de memoria puede aumentar.  
  
### <a name="remarks"></a>Comentarios  
 Si *bAllowGrow* es distinto de cero, aumenta el tamaño del bloque de memoria según sea necesario, por ejemplo, si un intento no se intentó escribir más bytes en el archivo que se le ha asignado para el bloque de memoria.  
  
## <a name="see-also"></a>Vea también  
 [Clase CMemFile](../../mfc/reference/cmemfile-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CMemFile (clase)](../../mfc/reference/cmemfile-class.md)
