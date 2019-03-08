---
title: CMemFile (clase)
ms.date: 11/04/2016
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
helpviewer_keywords:
- CMemFile [MFC], CMemFile
- CMemFile [MFC], Attach
- CMemFile [MFC], Detach
- CMemFile [MFC], Alloc
- CMemFile [MFC], Free
- CMemFile [MFC], GrowFile
- CMemFile [MFC], Memcpy
- CMemFile [MFC], Realloc
ms.assetid: 20e86515-e465-4f73-b2ea-e49789d63165
ms.openlocfilehash: a57f4e245ca1e93ec0edd454a7f407aeda5beca4
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57304952"
---
# <a name="cmemfile-class"></a>CMemFile (clase)

El [CFile](../../mfc/reference/cfile-class.md)-clase derivada que admite archivos de memoria.

## <a name="syntax"></a>Sintaxis

```
class CMemFile : public CFile
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CMemFile::CMemFile](#cmemfile)|Construye un objeto de archivo de memoria.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CMemFile::Attach](#attach)|Asocia un bloque de memoria a `CMemFile`.|
|[CMemFile::Detach](#detach)|Desasocia el bloque de memoria de `CMemFile` y devuelve un puntero al bloque de memoria desasociado.|

### <a name="protected-methods"></a>Métodos protegidos

|Name|Descripción|
|----------|-----------------|
|[CMemFile::Alloc](#alloc)|Invalide para modificar el comportamiento de asignación de memoria.|
|[CMemFile::Free](#free)|Invalide para modificar el comportamiento de desasignación de memoria.|
|[CMemFile::GrowFile](#growfile)|Invalide para modificar el comportamiento cuando un archivo.|
|[CMemFile::Memcpy](#memcpy)|Invalide para modificar el comportamiento de copia de memoria al leer y escribir archivos.|
|[CMemFile::Realloc](#realloc)|Invalide para modificar el comportamiento de la reasignación de memoria.|

## <a name="remarks"></a>Comentarios

Estos archivos de memoria se comportan como los archivos de disco, salvo que el archivo se almacena en la memoria RAM en lugar de en disco. Un archivo de memoria es útil para el almacenamiento temporal rápido o para la transferencia de bytes sin formato o los objetos serializados entre procesos independientes.

`CMemFile` los objetos pueden asignar automáticamente su propia memoria o puede adjuntar su propio bloque de memoria para el `CMemFile` objeto mediante una llamada a [adjuntar](#attach). En cualquier caso, se asigna memoria para aumentar automáticamente el archivo de memoria en `nGrowBytes`-tamaño incrementos si `nGrowBytes` no es cero.

El bloque de memoria se eliminarán automáticamente tras la destrucción de la `CMemFile` objeto si la memoria se asignó originalmente por el `CMemFile` objeto; en caso contrario, es responsable de desasignar la memoria que adjunta al objeto.

Puede tener acceso el bloque de memoria a través del puntero proporcionado cuando se separa de la `CMemFile` objeto mediante una llamada a [Detach](#detach).

El uso más común de `CMemFile` consiste en crear un `CMemFile` objeto y su uso mediante una llamada a [CFile](../../mfc/reference/cfile-class.md) funciones miembro. Tenga en cuenta que la creación un `CMemFile` lo abre automáticamente: no se llame a [CFile::Open](../../mfc/reference/cfile-class.md#open), que se usa solo para archivos de disco. Dado que `CMemFile` no usa un archivo de disco, el miembro de datos `CFile::m_hFile` no se utiliza.

El `CFile` funciones miembro [duplicar](../../mfc/reference/cfile-class.md#duplicate), [LockRange](../../mfc/reference/cfile-class.md#lockrange), y [UnlockRange](../../mfc/reference/cfile-class.md#unlockrange) no se implementan para `CMemFile`. Si se llama a estas funciones en un `CMemFile` objeto, obtendrá un [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).

`CMemFile` usa las funciones de biblioteca de tiempo de ejecución [malloc](../../c-runtime-library/reference/malloc.md), [realloc](../../c-runtime-library/reference/realloc.md), y [libre](../../c-runtime-library/reference/free.md) para asignar, reasignar y desasignar memoria; y la función intrínseca [memcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md) al bloque de memoria de copia al leer y escribir. Si desea cambiar este comportamiento o el comportamiento cuando `CMemFile` crece a un archivo, derive su propia clase de `CMemFile` e invalidar las funciones adecuadas.

Para obtener más información sobre `CMemFile`, consulte los artículos [archivos en MFC](../../mfc/files-in-mfc.md) y [administración de memoria (MFC)](../../mfc/memory-management.md) y vea [manejo de archivos](../../c-runtime-library/file-handling.md) en el *tiempo de ejecución Referencia de la biblioteca*.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

`CMemFile`

## <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

##  <a name="alloc"></a>  CMemFile::Alloc

Esta función se invoca `CMemFile` funciones miembro.

```
virtual BYTE* Alloc(SIZE_T nBytes);
```

### <a name="parameters"></a>Parámetros

*nBytes*<br/>
Número de bytes de asignación de memoria.

### <a name="return-value"></a>Valor devuelto

Un puntero al bloque de memoria que se ha asignado, o NULL si no se pudo la asignación.

### <a name="remarks"></a>Comentarios

Reemplace esta función para implementar la asignación de memoria personalizado. Si reemplaza esta función, probablemente deseará reemplazar [gratis](#free) y [Realloc](#realloc) también.

La implementación predeterminada usa la función de biblioteca de tiempo de ejecución [malloc](../../c-runtime-library/reference/malloc.md) para asignar memoria.

##  <a name="attach"></a>  CMemFile::Attach

Llame a esta función para adjuntar un bloque de memoria a `CMemFile`.

```
void Attach(
    BYTE* lpBuffer,
    UINT nBufferSize,
    UINT nGrowBytes = 0);
```

### <a name="parameters"></a>Parámetros

*lpBuffer*<br/>
Puntero al búfer que se adjuntará a `CMemFile`.

*nBufferSize*<br/>
Un entero que especifica el tamaño del búfer en bytes.

*nGrowBytes*<br/>
El incremento de la asignación de memoria en bytes.

### <a name="remarks"></a>Comentarios

Esto hace que `CMemFile` para usar el bloque de memoria que el archivo de memoria.

Si *nGrowBytes* es 0, `CMemFile` establecerá la longitud del archivo en *nBufferSize*. Esto significa que los datos del bloque de memoria antes de se ha adjuntado a `CMemFile` se usará como el archivo. No pueden crecer los archivos de memoria creados de esta manera.

Dado que el archivo no puede ser crece, tenga cuidado para no generar `CMemFile` para intentar expandir el archivo. Por ejemplo, no llame a la `CMemFile` invalidaciones de [CFile:Write](../../mfc/reference/cfile-class.md#write) para escribir más allá del final o no llame a [CFile:SetLength](../../mfc/reference/cfile-class.md#setlength) con una longitud mayor *nBufferSize*.

Si *nGrowBytes* es mayor que 0, `CMemFile` pasará por alto el contenido del bloque de memoria que se haya asociado. Tendrá que escribir el contenido del archivo de memoria desde cero mediante el `CMemFile` la invalidación de `CFile::Write`. Si se intenta escribir más allá del final del archivo aumente o disminuya el archivo mediante una llamada a la `CMemFile` la invalidación de `CFile::SetLength`, `CMemFile` aumentará la asignación de memoria en incrementos de *nGrowBytes*. Aumentar la asignación de memoria se producirá un error si el bloque de memoria que se pasa a `Attach` no se ha asignado con un método compatible con [Alloc](#alloc). Para que sea compatible con la implementación predeterminada de `Alloc`, debe asignar la memoria con la función de biblioteca de tiempo de ejecución [malloc](../../c-runtime-library/reference/malloc.md) o [calloc](../../c-runtime-library/reference/calloc.md).

##  <a name="cmemfile"></a>  CMemFile::CMemFile

La primera sobrecarga abre un archivo de memoria vacío.

```
CMemFile(UINT nGrowBytes = 1024);

CMemFile(
    BYTE* lpBuffer,
    UINT nBufferSize,
    UINT nGrowBytes = 0);
```

### <a name="parameters"></a>Parámetros

*nGrowBytes*<br/>
El incremento de la asignación de memoria en bytes.

*lpBuffe*r puntero a un búfer que recibe información del tamaño *nBufferSize*.

*nBufferSize*<br/>
Un entero que especifica el tamaño del búfer del archivo, en bytes.

### <a name="remarks"></a>Comentarios

Tenga en cuenta que el archivo se abre en el constructor y que no debe llamar [CFile::Open](../../mfc/reference/cfile-class.md#open).

La segunda sobrecarga actúa igual como si se usa el primer constructor y se llama inmediatamente a [adjuntar](#attach) con los mismos parámetros. Para obtener información más detallada, vea `Attach`.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#36](../../atl-mfc-shared/reference/codesnippet/cpp/cmemfile-class_1.cpp)]

##  <a name="detach"></a>  CMemFile::Detach

Llame a esta función para obtener un puntero al bloque de memoria que usa `CMemFile`.

```
BYTE* Detach();
```

### <a name="return-value"></a>Valor devuelto

Un puntero al bloque de memoria que contiene el contenido del archivo de memoria.

### <a name="remarks"></a>Comentarios

Llamar a esta función también se cierra el `CMemFile`. Puede volver a adjuntar el bloque de memoria `CMemFile` mediante una llamada a [adjuntar](#attach). Si desea volver a adjuntar el archivo y usar los datos en él, debe llamar a [CFile::GetLength](../../mfc/reference/cfile-class.md#getlength) para obtener la longitud del archivo antes de llamar a `Detach`. Tenga en cuenta que si se conecta a un bloque de memoria `CMemFile` para que pueda usar sus datos ( `nGrowBytes` == 0), entonces no podrá crecer el archivo de memoria.

##  <a name="free"></a>  CMemFile::Free

Esta función se invoca `CMemFile` funciones miembro.

```
virtual void Free(BYTE* lpMem);
```

### <a name="parameters"></a>Parámetros

*lpMem*<br/>
Puntero a la memoria que se va a cancelar la asignación.

### <a name="remarks"></a>Comentarios

Reemplace esta función para implementar la desasignación de memoria personalizado. Si reemplaza esta función, probablemente deseará reemplazar [Alloc](#alloc) y [Realloc](#realloc) también.

##  <a name="growfile"></a>  CMemFile::GrowFile

Esta función se invoca por algunos de los `CMemFile` funciones miembro.

```
virtual void GrowFile(SIZE_T dwNewLen);
```

### <a name="parameters"></a>Parámetros

*dwNewLen*<br/>
Nuevo tamaño del archivo de memoria.

### <a name="remarks"></a>Comentarios

Puede invalidar si desea cambiar cómo `CMemFile` crece su archivo. La implementación predeterminada llama [Realloc](#realloc) crezca un bloque existente (o [Alloc](#alloc) para crear un bloque de memoria), la asignación de memoria en múltiplos de la `nGrowBytes` valor especificado en el constructor o [Adjuntar](#attach) llamar.

##  <a name="memcpy"></a>  CMemFile::Memcpy

Esta función se llama mediante el `CMemFile` invalidaciones de [CFile:: Read](../../mfc/reference/cfile-class.md#read) y [CFile::Write](../../mfc/reference/cfile-class.md#write) para transferir datos hacia y desde el archivo de memoria.

```
virtual BYTE* Memcpy(
    BYTE* lpMemTarget,
    const BYTE* lpMemSource,
    SIZE_T nBytes);
```

### <a name="parameters"></a>Parámetros

*lpMemTarget*<br/>
Puntero al bloque de memoria en la que se copiará la memoria de origen.

*lpMemSource*<br/>
Puntero al bloque de memoria de origen.

*nBytes*<br/>
Número de bytes que se van a copiar.

### <a name="return-value"></a>Valor devuelto

Una copia de *lpMemTarget*.

### <a name="remarks"></a>Comentarios

Reemplace esta función si desea cambiar la forma en que `CMemFile` estas copias de la memoria.

##  <a name="realloc"></a>  CMemFile::Realloc

Esta función se invoca `CMemFile` funciones miembro.

```
virtual BYTE* Realloc(
    BYTE* lpMem,
    SIZE_T nBytes);
```

### <a name="parameters"></a>Parámetros

*lpMem*<br/>
Un puntero al bloque de memoria se asignen de nuevo.

*nBytes*<br/>
Nuevo tamaño de bloque de memoria.

### <a name="return-value"></a>Valor devuelto

Un puntero al bloque de memoria reasignado (y, posiblemente, trasladado), o NULL si no se pudo la reasignación.

### <a name="remarks"></a>Comentarios

Reemplace esta función para implementar la reasignación de memoria personalizado. Si reemplaza esta función, probablemente deseará reemplazar [Alloc](#alloc) y [gratis](#free) también.

## <a name="see-also"></a>Vea también

[CFile (clase)](../../mfc/reference/cfile-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
