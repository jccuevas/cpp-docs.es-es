---
title: Clase CSharedFile | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSharedFile
dev_langs:
- C++
helpviewer_keywords:
- memory files
- CSharedFile class
- shared memory files
ms.assetid: 5d000422-9ede-4318-a8c9-f7412b674f39
caps.latest.revision: 21
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: f812b2c7b8e3b158068bf3fdab0a327460056251
ms.lasthandoff: 02/24/2017

---
# <a name="csharedfile-class"></a>Clase CSharedFile
El [CMemFile](../../mfc/reference/cmemfile-class.md)-clase derivada que admite archivos de memoria compartida.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CSharedFile : public CMemFile  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CSharedFile::CSharedFile](#csharedfile)|Construye un objeto `CSharedFile`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CSharedFile::Detach](#detach)|Cierra el archivo de memoria compartida y devuelve el identificador de su bloque de memoria.|  
|[CSharedFile::SetHandle](#sethandle)|Adjunta el archivo de memoria compartida a un bloque de memoria.|  
  
## <a name="remarks"></a>Comentarios  
 Archivos de memoria se comportan como archivos de disco, excepto en que el archivo se almacena en RAM, en lugar de en disco. Un archivo de memoria es útil para el almacenamiento temporal rápido o para la transferencia de bytes sin formato u objetos serializados entre procesos independientes.  
  
 Archivos de memoria compartida a diferencia de otros archivos de la memoria se asigna memoria para ellos con el [GlobalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366574) función de Windows. El `CSharedFile` clase almacena datos en un bloque de memoria asignado globalmente (creado con **GlobalAlloc**), y este bloque de memoria se puede compartir con DDE, el Portapapeles o demás OLE/COM uniforme transferencia operaciones de datos, por ejemplo, mediante `IDataObject`.  
  
 **GlobalAlloc** devuelve un `HGLOBAL` controlar en lugar de un puntero a la memoria, como el puntero devuelto por [malloc](../../c-runtime-library/reference/malloc.md). El `HGLOBAL` identificador necesario en ciertas aplicaciones. Por ejemplo, para colocar datos en el Portapapeles necesita un `HGLOBAL` controlar.  
  
 Tenga en cuenta que `CSharedFile` no asignado a la memoria de uso de archivos y los datos no se puede compartir directamente entre los procesos.  
  
 `CSharedFile`objetos pueden asignar automáticamente a su propia memoria o puede adjuntar su propio bloque de memoria a la `CSharedFile` objeto mediante una llamada a [CSharedFile::SetHandle](#sethandle). En cualquier caso, se asigna memoria para aumentar el archivo de memoria automáticamente en `nGrowBytes`-tamaño incrementos si `nGrowBytes` no es cero.  
  
 Para obtener más información, vea el artículo [archivos en MFC](../../mfc/files-in-mfc.md) y [administración de archivos](../../c-runtime-library/file-handling.md) en el *referencia de la biblioteca de tiempo de ejecución*.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 [CMemFile](../../mfc/reference/cmemfile-class.md)  
  
 `CSharedFile`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxadv.h  
  
##  <a name="a-namecsharedfilea--csharedfilecsharedfile"></a><a name="csharedfile"></a>CSharedFile::CSharedFile  
 Construye un `CSharedFile` de objeto y le asigna memoria.  
  
```  
CSharedFile(
    UINT nAllocFlags = GMEM_DDESHARE | GMEM_MOVEABLE,  
    UINT nGrowBytes = 4096);
```  
  
### <a name="parameters"></a>Parámetros  
 *nAllocFlags*  
 Marcas que indica cómo se puede asignar memoria. Consulte [GlobalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366574) para obtener una lista de valores de indicador válidos.  
  
 `nGrowBytes`  
 El incremento de la asignación de memoria en bytes.  
  
##  <a name="a-namedetacha--csharedfiledetach"></a><a name="detach"></a>CSharedFile::Detach  
 Llame a esta función para cerrar el archivo de memoria y desconectar desde el bloque de memoria.  
  
```  
HGLOBAL Detach();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador del bloque de memoria que contiene el contenido del archivo de memoria.  
  
### <a name="remarks"></a>Comentarios  
 Puede volver a abrirlo llamando a [SetHandle](#sethandle), utilizando el identificador devuelto por **separar**.  
  
##  <a name="a-namesethandlea--csharedfilesethandle"></a><a name="sethandle"></a>CSharedFile::SetHandle  
 Llame a esta función para adjuntar un bloque de memoria global para la `CSharedFile` objeto.  
  
```  
void SetHandle(
    HGLOBAL hGlobalMemory,  
    BOOL bAllowGrow = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 *hGlobalMemory*  
 Identificador de la memoria global para adjuntarlo a la `CSharedFile`.  
  
 `bAllowGrow`  
 Especifica si el bloque de memoria se puede aumentar de tamaño.  
  
### <a name="remarks"></a>Comentarios  
 Si `bAllowGrow` se realiza es distinto de cero, aumenta el tamaño del bloque de memoria según sea necesario, por ejemplo, si se intenta escribir más bytes en el archivo que se ha asignado para el bloque de memoria.  
  
## <a name="see-also"></a>Vea también  
 [Clase CMemFile](../../mfc/reference/cmemfile-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clase CMemFile](../../mfc/reference/cmemfile-class.md)

