---
title: Clase CMemFile | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMemFile
- AFX/CMemFile
- AFX/CMemFile::CMemFile
- AFX/CMemFile::Attach
- AFX/CMemFile::Detach
- AFX/CMemFile::Alloc
- AFX/CMemFile::Free
- AFX/CMemFile::GrowFile
- AFX/CMemFile::Memcpy
- AFX/CMemFile::Realloc
dev_langs:
- C++
helpviewer_keywords:
- memory files
- CMemFile class
- temporary files, memory files
ms.assetid: 20e86515-e465-4f73-b2ea-e49789d63165
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 9851e050b05ac129e5e498c7ea99dfedddc79e54
ms.lasthandoff: 02/24/2017

---
# <a name="cmemfile-class"></a>Clase CMemFile
El [CFile](../../mfc/reference/cfile-class.md)-clase derivada que admite archivos de memoria.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMemFile : public CFile  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMemFile::CMemFile](#cmemfile)|Construye un objeto de archivo de memoria.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMemFile::Attach](#attach)|Asocia un bloque de memoria a `CMemFile`.|  
|[CMemFile::Detach](#detach)|Desasocia el bloque de memoria de `CMemFile` y devuelve un puntero al bloque de memoria separado.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMemFile::Alloc](#alloc)|Invalidar para modificar el comportamiento de asignación de memoria.|  
|[CMemFile::Free](#free)|Invalidar para modificar el comportamiento de desasignación de memoria.|  
|[CMemFile::GrowFile](#growfile)|Invalidar para modificar el comportamiento cuando un archivo.|  
|[CMemFile::Memcpy](#memcpy)|Invalidar para modificar el comportamiento de copia de memoria al leer y escribir archivos.|  
|[CMemFile::Realloc](#realloc)|Invalidar para modificar el comportamiento de reasignación de memoria.|  
  
## <a name="remarks"></a>Comentarios  
 Estos archivos de memoria se comportan como archivos de disco, excepto en que el archivo se almacena en RAM, en lugar de en disco. Un archivo de memoria es útil para el almacenamiento temporal rápido o para la transferencia de bytes sin formato u objetos serializados entre procesos independientes.  
  
 `CMemFile`objetos pueden asignar automáticamente a su propia memoria o puede adjuntar su propio bloque de memoria a la `CMemFile` objeto mediante una llamada a [adjuntar](#attach). En cualquier caso, se asigna memoria para aumentar el archivo de memoria automáticamente en `nGrowBytes`-tamaño incrementos si `nGrowBytes` no es cero.  
  
 El bloque de memoria se eliminarán automáticamente tras la destrucción de la `CMemFile` objeto si la memoria se asignó originalmente por el `CMemFile` objeto; en caso contrario, es responsable de desasignar la memoria que se adjunta al objeto.  
  
 Puede tener acceso el bloque de memoria a través del puntero proporcionado cuando se separa de la `CMemFile` objeto mediante una llamada a [separar](#detach).  
  
 El uso más común de `CMemFile` es crear un `CMemFile` de objetos y utilizar llamando a [CFile](../../mfc/reference/cfile-class.md) funciones miembro. Tenga en cuenta que crear un `CMemFile` lo abre automáticamente: no se llama [CFile::Open](../../mfc/reference/cfile-class.md#open), que se usa solo para los archivos de disco. Porque `CMemFile` no usa un archivo de disco, el miembro de datos `CFile::m_hFile` no se utiliza.  
  
 El `CFile` funciones miembro [duplicar](../../mfc/reference/cfile-class.md#duplicate), [LockRange](../../mfc/reference/cfile-class.md#lockrange), y [UnlockRange](../../mfc/reference/cfile-class.md#unlockrange) no se implementan para `CMemFile`. Si se llama a estas funciones en una `CMemFile` objeto, obtendrá un [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).  
  
 `CMemFile`usa las funciones de biblioteca de tiempo de ejecución [malloc](../../c-runtime-library/reference/malloc.md), [realloc](../../c-runtime-library/reference/realloc.md), y [libre](../../c-runtime-library/reference/free.md) para asignar, asignar y desasignar memoria; y la función intrínseca [memcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md) al bloque de memoria de copia al leer y escribir. Si desea cambiar este comportamiento o el comportamiento cuando `CMemFile` crece a un archivo, derive su propia clase de `CMemFile` e invalidar las funciones adecuadas.  
  
 Para obtener más información sobre `CMemFile`, consulte los artículos [archivos en MFC](../../mfc/files-in-mfc.md) y [administración de memoria (MFC)](../../mfc/memory-management.md) y vea [administración de archivos](../../c-runtime-library/file-handling.md) en el *referencia de la biblioteca de tiempo de ejecución*.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 `CMemFile`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h  
  
##  <a name="alloc"></a>CMemFile::Alloc  
 Esta función se invoca `CMemFile` funciones miembro.  
  
```  
virtual BYTE* Alloc(SIZE_T nBytes);
```  
  
### <a name="parameters"></a>Parámetros  
 `nBytes`  
 Número de bytes de asignación de memoria.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al bloque de memoria asignada, o **NULL** si la asignación de errores.  
  
### <a name="remarks"></a>Comentarios  
 Reemplazar esta función para implementar la asignación de memoria personalizado. Si reemplaza esta función, probablemente deseará reemplazar [gratis](#free) y [Realloc](#realloc) también.  
  
 La implementación predeterminada usa la función de biblioteca en tiempo de ejecución [malloc](../../c-runtime-library/reference/malloc.md) para asignar memoria.  
  
##  <a name="attach"></a>CMemFile::Attach  
 Llame a esta función para adjuntar un bloque de memoria a `CMemFile`.  
  
```  
void Attach(
    BYTE* lpBuffer,  
    UINT nBufferSize,  
    UINT nGrowBytes = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpBuffer`  
 Puntero al búfer que se adjuntará a `CMemFile`.  
  
 `nBufferSize`  
 Un entero que especifica el tamaño del búfer en bytes.  
  
 `nGrowBytes`  
 El incremento de la asignación de memoria en bytes.  
  
### <a name="remarks"></a>Comentarios  
 Esto hace que `CMemFile` para usar el bloque de memoria que el archivo de memoria.  
  
 Si `nGrowBytes` es 0, `CMemFile` establecerá la longitud del archivo en `nBufferSize`. Esto significa que los datos del bloque de memoria antes de que se adjuntó a `CMemFile` se usará como el archivo. No pueden crecer los archivos de memoria creados de esta manera.  
  
 Puesto que el archivo no se puede incrementar, tenga cuidado de no provocar `CMemFile` para intentar expandir el archivo. Por ejemplo, no llame a la `CMemFile` invalidaciones de [CFile:Write](../../mfc/reference/cfile-class.md#write) para escribir más allá del final o no llamar a [CFile:SetLength](../../mfc/reference/cfile-class.md#setlength) con una longitud mayor que `nBufferSize`.  
  
 Si `nGrowBytes` es mayor que 0, `CMemFile` ignorará el contenido del bloque de memoria que se haya asociado. Tendrá que escribir el contenido del archivo de memoria desde cero mediante la `CMemFile` la invalidación de `CFile::Write`. Si se intenta escribir más allá del final del archivo o expandir el archivo llamando a la `CMemFile` la invalidación de `CFile::SetLength`, `CMemFile` aumentará la asignación de memoria en incrementos de `nGrowBytes`. Crecimiento de la asignación de memoria se producirá un error si el bloque de memoria se pasa a **adjuntar** no se asignan a un método compatible con [Alloc](#alloc). Para ser compatible con la implementación predeterminada de `Alloc`, debe asignar la memoria con la función de biblioteca en tiempo de ejecución [malloc](../../c-runtime-library/reference/malloc.md) o [calloc](../../c-runtime-library/reference/calloc.md).  
  
##  <a name="cmemfile"></a>CMemFile::CMemFile  
 La primera sobrecarga abre un archivo de memoria vacío.  
  
```  
CMemFile(UINT nGrowBytes = 1024);

 
CMemFile(
    BYTE* lpBuffer,  
    UINT nBufferSize,  
    UINT nGrowBytes = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 `nGrowBytes`  
 El incremento de la asignación de memoria en bytes.  
  
 *lpBuffe*r  
 Puntero a un búfer que recibe la información del tamaño `nBufferSize`.  
  
 `nBufferSize`  
 Un entero que especifica el tamaño del búfer del archivo, en bytes.  
  
### <a name="remarks"></a>Comentarios  
 Tenga en cuenta que el archivo está abierto, el constructor y que no debería llamar [CFile::Open](../../mfc/reference/cfile-class.md#open).  
  
 La segunda sobrecarga actúa igual que si utiliza el primer constructor y llama inmediatamente a [asociar](#attach) con los mismos parámetros. Consulte **adjuntar** para obtener más información.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCFiles&#36;](../../atl-mfc-shared/reference/codesnippet/cpp/cmemfile-class_1.cpp)]  
  
##  <a name="detach"></a>CMemFile::Detach  
 Llame a esta función para obtener un puntero al bloque de memoria que utiliza `CMemFile`.  
  
```  
BYTE* Detach();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al bloque de memoria que contiene el contenido del archivo de memoria.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a esta función también se cierra el `CMemFile`. Puede volver a adjuntar el bloque de memoria `CMemFile` llamando a [adjuntar](#attach). Si desea volver a adjuntar el archivo y utilizar los datos en él, debe llamar a [CFile::GetLength](../../mfc/reference/cfile-class.md#getlength) para obtener la longitud del archivo antes de llamar a **separar**. Tenga en cuenta que si se conecta a un bloque de memoria `CMemFile` para que pueda usar sus datos ( `nGrowBytes` == 0), entonces no podrá crecer el archivo de memoria.  
  
##  <a name="free"></a>CMemFile::Free  
 Esta función se invoca `CMemFile` funciones miembro.  
  
```  
virtual void Free(BYTE* lpMem);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpMem`  
 Puntero a la memoria que se va a cancelar la asignación de *.*  
  
### <a name="remarks"></a>Comentarios  
 Reemplazar esta función para implementar la desasignación de memoria personalizado. Si reemplaza esta función, probablemente deseará reemplazar [Alloc](#alloc) y [Realloc](#realloc) también.  
  
##  <a name="growfile"></a>CMemFile::GrowFile  
 Esta función se invoca por algunos de los `CMemFile` funciones miembro.  
  
```  
virtual void GrowFile(SIZE_T dwNewLen);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwNewLen`  
 Nuevo tamaño del archivo de memoria.  
  
### <a name="remarks"></a>Comentarios  
 Se puede reemplazar si desea cambiar cómo `CMemFile` crece su archivo. La implementación predeterminada llama [Realloc](#realloc) crecer un bloque existente (o [Alloc](#alloc) para crear un bloque de memoria), la asignación de memoria en múltiplos de la `nGrowBytes` valor especificado en el constructor o [adjuntar](#attach) llamar.  
  
##  <a name="memcpy"></a>CMemFile::Memcpy  
 Esta función es invocada por el `CMemFile` invalidaciones de [CFile:: Read](../../mfc/reference/cfile-class.md#read) y [CFile::Write](../../mfc/reference/cfile-class.md#write) para transferir datos hacia y desde el archivo de memoria.  
  
```  
virtual BYTE* Memcpy(
    BYTE* lpMemTarget,  
    const BYTE* lpMemSource,  
    SIZE_T nBytes);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpMemTarget`  
 Puntero al bloque de memoria en la que se van a copiar la memoria de origen.  
  
 `lpMemSource`  
 Puntero al bloque de memoria de origen.  
  
 `nBytes`  
 Número de bytes que se van a copiar.  
  
### <a name="return-value"></a>Valor devuelto  
 Una copia de la clase `lpMemTarget`.  
  
### <a name="remarks"></a>Comentarios  
 Reemplace esta función si desea cambiar la forma en que `CMemFile` estas copias en memoria.  
  
##  <a name="realloc"></a>CMemFile::Realloc  
 Esta función se invoca `CMemFile` funciones miembro.  
  
```  
virtual BYTE* Realloc(
    BYTE* lpMem,  
    SIZE_T nBytes);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpMem`  
 Un puntero al bloque de memoria se reasignen.  
  
 `nBytes`  
 Nuevo tamaño de bloque de memoria.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al bloque de memoria que se reasignen (y posiblemente mueve), o **NULL** si falla la reasignación.  
  
### <a name="remarks"></a>Comentarios  
 Reemplazar esta función para implementar la reasignación de memoria personalizado. Si reemplaza esta función, probablemente deseará reemplazar [Alloc](#alloc) y [gratis](#free) también.  
  
## <a name="see-also"></a>Vea también  
 [CFile (clase)](../../mfc/reference/cfile-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)




