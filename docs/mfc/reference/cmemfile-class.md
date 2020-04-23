---
title: Clase CMemFile
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
ms.openlocfilehash: 1bd88ad17bdb047de4c344ab96f3d9aecbe23c31
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752637"
---
# <a name="cmemfile-class"></a>Clase CMemFile

La clase derivada de [CFile](../../mfc/reference/cfile-class.md)que admite archivos de memoria.

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
|[CMemFile::Attach](#attach)|Asocia un bloque de `CMemFile`memoria a .|
|[CMemFile::Detach](#detach)|Separa el bloque de `CMemFile` memoria y devuelve un puntero al bloque de memoria separado.|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CMemFile::Alloc](#alloc)|Reemplazar para modificar el comportamiento de asignación de memoria.|
|[CMemFile::Gratis](#free)|Reemplazar para modificar el comportamiento de desasignación de memoria.|
|[CMemFile::GrowFile](#growfile)|Reemplazar para modificar el comportamiento al crear un archivo.|
|[CMemFile::Memcpy](#memcpy)|Reemplazar para modificar el comportamiento de copia de memoria al leer y escribir archivos.|
|[CMemFile::Realloc](#realloc)|Reemplazar para modificar el comportamiento de reasignación de memoria.|

## <a name="remarks"></a>Observaciones

Estos archivos de memoria se comportan como archivos de disco, excepto que el archivo se almacena en RAM en lugar de en el disco. Un archivo de memoria es útil para el almacenamiento temporal rápido o para transferir bytes sin procesar u objetos serializados entre procesos independientes.

`CMemFile`los objetos pueden asignar automáticamente su propia memoria `CMemFile` o puede adjuntar su propio bloque de memoria al objeto llamando a [Attach](#attach). En cualquier caso, la memoria para aumentar `nGrowBytes`el archivo `nGrowBytes` de memoria automáticamente se asigna en incrementos de tamaño si no es cero.

El bloque de memoria se eliminará `CMemFile` automáticamente tras la destrucción `CMemFile` del objeto si el objeto asignó originalmente la memoria; de lo contrario, usted es responsable de desasignar la memoria que adjuntó al objeto.

Puede tener acceso al bloque de memoria a través del puntero proporcionado al separarlo del `CMemFile` objeto llamando a [Separar](#detach).

El uso más `CMemFile` común de `CMemFile` es crear un objeto y usarlo mediante una llamada a [CFile](../../mfc/reference/cfile-class.md) funciones miembro. Tenga en `CMemFile` cuenta que la creación de un lo abre automáticamente: no se llama a [CFile::Open](../../mfc/reference/cfile-class.md#open), que solo se utiliza para archivos de disco. Dado `CMemFile` que no usa un archivo `CFile::m_hFile` de disco, no se usa el miembro de datos.

Las `CFile` funciones miembro [Duplicate](../../mfc/reference/cfile-class.md#duplicate), [LockRange](../../mfc/reference/cfile-class.md#lockrange)y `CMemFile` [UnlockRange](../../mfc/reference/cfile-class.md#unlockrange) no se implementan para . Si llama a estas `CMemFile` funciones en un objeto, obtendrá una [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).

`CMemFile`utiliza las funciones de biblioteca en tiempo de ejecución [malloc](../../c-runtime-library/reference/malloc.md), [realloc](../../c-runtime-library/reference/realloc.md)y [free](../../c-runtime-library/reference/free.md) para asignar, reasignar y desasignar memoria; y el [memcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md) intrínseco para bloquear la memoria de copia al leer y escribir. Si desea cambiar este comportamiento o el `CMemFile` comportamiento cuando crece un `CMemFile` archivo, derive su propia clase de las funciones adecuadas e invalide las funciones adecuadas.

Para obtener `CMemFile`más información sobre , vea los artículos [Archivos en MFC](../../mfc/files-in-mfc.md) y Administración de memoria [(MFC)](../../mfc/memory-management.md) y [Control](../../c-runtime-library/file-handling.md) de archivos en la referencia de la biblioteca en tiempo *de ejecución*.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

`CMemFile`

## <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

## <a name="cmemfilealloc"></a><a name="alloc"></a>CMemFile::Alloc

Las funciones `CMemFile` miembro llaman a esta función.

```
virtual BYTE* Alloc(SIZE_T nBytes);
```

### <a name="parameters"></a>Parámetros

*nBytes*<br/>
Número de bytes de memoria que se asignarán.

### <a name="return-value"></a>Valor devuelto

Puntero al bloque de memoria asignado, o NULL si se produjo un error en la asignación.

### <a name="remarks"></a>Observaciones

Invalide esta función para implementar la asignación de memoria personalizada. Si invalida esta función, probablemente querrá reemplazar [Free](#free) y [Realloc](#realloc) también.

La implementación predeterminada utiliza la función [malloc](../../c-runtime-library/reference/malloc.md) de biblioteca en tiempo de ejecución para asignar memoria.

## <a name="cmemfileattach"></a><a name="attach"></a>CMemFile::Attach

Llame a esta función para `CMemFile`adjuntar un bloque de memoria a .

```cpp
void Attach(
    BYTE* lpBuffer,
    UINT nBufferSize,
    UINT nGrowBytes = 0);
```

### <a name="parameters"></a>Parámetros

*lpBuffer*<br/>
Puntero al búfer que `CMemFile`se va a asociar a .

*nBufferSize*<br/>
Entero que especifica el tamaño del búfer en bytes.

*nGrowBytes*<br/>
El incremento de asignación de memoria en bytes.

### <a name="remarks"></a>Observaciones

Esto `CMemFile` hace que se utilice el bloque de memoria como archivo de memoria.

Si *nGrowBytes* es `CMemFile` 0, establecerá la longitud del archivo en *nBufferSize*. Esto significa que los datos del bloque `CMemFile` de memoria antes de que se adjuntaran se utilizarán como archivo. Los archivos de memoria creados de esta manera no se pueden cultivar.

Puesto que el archivo no se `CMemFile` puede cultivar, tenga cuidado de no hacer para intentar hacer crecer el archivo. Por ejemplo, no llame `CMemFile` a las invalidaciones de [CFile:Write](../../mfc/reference/cfile-class.md#write) para escribir más allá del final o no llame a [CFile:SetLength](../../mfc/reference/cfile-class.md#setlength) con una longitud mayor que *nBufferSize*.

Si *nGrowBytes* es mayor `CMemFile` que 0, omitirá el contenido del bloque de memoria que ha adjuntado. Tendrás que escribir el contenido del archivo de `CMemFile` memoria `CFile::Write`desde cero usando la invalidación de . Si intenta escribir más allá del final del archivo `CMemFile` o `CFile::SetLength`aumentar `CMemFile` el archivo llamando a la invalidación de , aumentará la asignación de memoria en incrementos de *nGrowBytes*. Si el bloque de memoria al `Attach` que pasa no se ha asignado con un método compatible con [Alloc,](#alloc)se producirá un error al aumentar la asignación de memoria. Para ser compatible con `Alloc`la implementación predeterminada de , debe asignar la memoria con la función de biblioteca en tiempo de ejecución [malloc](../../c-runtime-library/reference/malloc.md) o [calloc](../../c-runtime-library/reference/calloc.md).

## <a name="cmemfilecmemfile"></a><a name="cmemfile"></a>CMemFile::CMemFile

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
El incremento de asignación de memoria en bytes.

*lpBuffe*r Puntero a un búfer que recibe información del tamaño *nBufferSize*.

*nBufferSize*<br/>
Entero que especifica el tamaño del búfer de archivos, en bytes.

### <a name="remarks"></a>Observaciones

Tenga en cuenta que el constructor abre el archivo y que no debe llamar a [CFile::Open](../../mfc/reference/cfile-class.md#open).

La segunda sobrecarga actúa igual que si se utiliza el primer constructor y se llama inmediatamente [Attach](#attach) con los mismos parámetros. Para obtener información detallada, vea `Attach`.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#36](../../atl-mfc-shared/reference/codesnippet/cpp/cmemfile-class_1.cpp)]

## <a name="cmemfiledetach"></a><a name="detach"></a>CMemFile::Detach

Llame a esta función para obtener un `CMemFile`puntero al bloque de memoria que está utilizando .

```
BYTE* Detach();
```

### <a name="return-value"></a>Valor devuelto

Puntero al bloque de memoria que contiene el contenido del archivo de memoria.

### <a name="remarks"></a>Observaciones

Al llamar a esta `CMemFile`función también se cierra el archivo . Puede volver a adjuntar `CMemFile` el bloque de memoria llamando a [Attach](#attach). Si desea volver a adjuntar el archivo y utilizar los datos en él, debe llamar a `Detach` [CFile::GetLength](../../mfc/reference/cfile-class.md#getlength) para obtener la longitud del archivo antes de llamar a . Tenga en cuenta que si `CMemFile` se adjunta un bloque `nGrowBytes` de memoria para que pueda utilizar sus datos ( .

## <a name="cmemfilefree"></a><a name="free"></a>CMemFile::Gratis

Las funciones `CMemFile` miembro llaman a esta función.

```
virtual void Free(BYTE* lpMem);
```

### <a name="parameters"></a>Parámetros

*lpMem*<br/>
Puntero a la memoria que se va a desasignar.

### <a name="remarks"></a>Observaciones

Invalide esta función para implementar la desasignación de memoria personalizada. Si invalida esta función, probablemente también querrá invalidar [Alloc](#alloc) y [Realloc.](#realloc)

## <a name="cmemfilegrowfile"></a><a name="growfile"></a>CMemFile::GrowFile

Esta función es llamada `CMemFile` por varias de las funciones miembro.

```
virtual void GrowFile(SIZE_T dwNewLen);
```

### <a name="parameters"></a>Parámetros

*dwNewLen*<br/>
Nuevo tamaño del archivo de memoria.

### <a name="remarks"></a>Observaciones

Puede invalidarlo si desea cambiar `CMemFile` el tamaño de su archivo. La implementación predeterminada llama a [Realloc](#realloc) para que crezca un bloque existente (o `nGrowBytes` [Alloc](#alloc) para crear un bloque de memoria), asignando memoria en múltiplos del valor especificado en el constructor o [Attach](#attach) llamada.

## <a name="cmemfilememcpy"></a><a name="memcpy"></a>CMemFile::Memcpy

Las invalidaciones de `CMemFile` [CFile::Read](../../mfc/reference/cfile-class.md#read) y [CFile::Write](../../mfc/reference/cfile-class.md#write) llaman a esta función para transferir datos desde y hacia el archivo de memoria.

```
virtual BYTE* Memcpy(
    BYTE* lpMemTarget,
    const BYTE* lpMemSource,
    SIZE_T nBytes);
```

### <a name="parameters"></a>Parámetros

*lpMemTarget*<br/>
Puntero al bloque de memoria en el que se copiará la memoria de origen.

*lpMemSource*<br/>
Puntero al bloque de memoria de origen.

*nBytes*<br/>
Número de bytes que se van a copiar.

### <a name="return-value"></a>Valor devuelto

Una copia de *lpMemTarget*.

### <a name="remarks"></a>Observaciones

Reemplace esta función si desea `CMemFile` cambiar la forma en que realiza estas copias de memoria.

## <a name="cmemfilerealloc"></a><a name="realloc"></a>CMemFile::Realloc

Las funciones `CMemFile` miembro llaman a esta función.

```
virtual BYTE* Realloc(
    BYTE* lpMem,
    SIZE_T nBytes);
```

### <a name="parameters"></a>Parámetros

*lpMem*<br/>
Puntero al bloque de memoria que se va a reasignar.

*nBytes*<br/>
Nuevo tamaño para el bloque de memoria.

### <a name="return-value"></a>Valor devuelto

Un puntero al bloque de memoria que se redondeó (y posiblemente se movió) o NULL si se produjo un error en la reasignación.

### <a name="remarks"></a>Observaciones

Invalide esta función para implementar la reasignación de memoria personalizada. Si invalida esta función, probablemente también querrá invalidar [Alloc](#alloc) y [Free.](#free)

## <a name="see-also"></a>Vea también

[CFile (clase)](../../mfc/reference/cfile-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
