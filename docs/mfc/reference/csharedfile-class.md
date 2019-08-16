---
title: Clase CSharedFile
ms.date: 11/04/2016
f1_keywords:
- CSharedFile
- AFXADV/CSharedFile
- AFXADV/CSharedFile::CSharedFile
- AFXADV/CSharedFile::Detach
- AFXADV/CSharedFile::SetHandle
helpviewer_keywords:
- CSharedFile [MFC], CSharedFile
- CSharedFile [MFC], Detach
- CSharedFile [MFC], SetHandle
ms.assetid: 5d000422-9ede-4318-a8c9-f7412b674f39
ms.openlocfilehash: 74a34ec169868d3e28f78f33da38dbda21ef23b3
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502611"
---
# <a name="csharedfile-class"></a>Clase CSharedFile

La clase derivada de [CMemFile](../../mfc/reference/cmemfile-class.md)que admite archivos de memoria compartidos.

## <a name="syntax"></a>Sintaxis

```
class CSharedFile : public CMemFile
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CSharedFile::CSharedFile](#csharedfile)|Construye un objeto `CSharedFile`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CSharedFile::Detach](#detach)|Cierra el archivo de memoria compartida y devuelve el identificador de su bloque de memoria.|
|[CSharedFile::SetHandle](#sethandle)|Adjunta el archivo de memoria compartida a un bloque de memoria.|

## <a name="remarks"></a>Comentarios

Los archivos de memoria se comportan como archivos de disco. La diferencia es que un archivo de memoria se almacena en RAM en lugar de en disco. Un archivo de memoria es útil para el almacenamiento temporal rápido, o para transferir bytes sin formato o objetos serializados entre procesos independientes.

Los archivos de memoria compartida se diferencian de otros archivos de memoria en esa memoria para que se asignen a la función de Windows [GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc) . La `CSharedFile` clase almacena los datos en un bloque de memoria asignado globalmente ( `GlobalAlloc`creado con), y este bloque de memoria se puede compartir mediante DDE, el portapapeles u otras operaciones de transferencia de datos uniformes OLE/ `IDataObject`com, por ejemplo, mediante.

`GlobalAlloc`Devuelve un identificador HGLOBAL en lugar de un puntero a la memoria, como el puntero devuelto por [malloc](../../c-runtime-library/reference/malloc.md). El identificador HGLOBAL es necesario en determinadas aplicaciones. Por ejemplo, para colocar datos en el portapapeles necesita un identificador HGLOBAL.

`CSharedFile`no utiliza archivos asignados a memoria y los datos no se pueden compartir directamente entre los procesos.

`CSharedFile`los objetos pueden asignar automáticamente su propia memoria. O bien, puede adjuntar su propio bloque de `CSharedFile` memoria al objeto llamando a [CSharedFile:: SetHandle](#sethandle). En cualquier caso, la memoria para el crecimiento automático del archivo de memoria `nGrowBytes`se asigna automáticamente a los `nGrowBytes` incrementos de tamaño si no es cero.

Para obtener más información, vea el artículo [archivos en MFC](../../mfc/files-in-mfc.md) y [control de archivos](../../c-runtime-library/file-handling.md) en la referencia de la biblioteca en tiempo de *ejecución*.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[CMemFile](../../mfc/reference/cmemfile-class.md)

`CSharedFile`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxadv. h

##  <a name="csharedfile"></a>  CSharedFile::CSharedFile

Construye un `CSharedFile` objeto y le asigna memoria.

```
CSharedFile(
    UINT nAllocFlags = GMEM_DDESHARE | GMEM_MOVEABLE,
    UINT nGrowBytes = 4096);
```

### <a name="parameters"></a>Parámetros

*nAllocFlags*<br/>
Marcas que indican cómo se va a asignar la memoria. Vea [GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc) para obtener una lista de valores de marca válidos.

*nGrowBytes*<br/>
El incremento de asignación de memoria en bytes.

##  <a name="detach"></a>  CSharedFile::Detach

Llame a esta función para cerrar el archivo de memoria y desasociarlo del bloque de memoria.

```
HGLOBAL Detach();
```

### <a name="return-value"></a>Valor devuelto

Identificador del bloque de memoria que incluye el contenido del archivo de memoria.

### <a name="remarks"></a>Comentarios

Puede volver a abrirlo llamando a [SetHandle](#sethandle), mediante el identificador devuelto por **detach**.

##  <a name="sethandle"></a>  CSharedFile::SetHandle

Llame a esta función para adjuntar un bloque de memoria `CSharedFile` global al objeto.

```
void SetHandle(
    HGLOBAL hGlobalMemory,
    BOOL bAllowGrow = TRUE);
```

### <a name="parameters"></a>Parámetros

*hGlobalMemory*<br/>
Identificador de la memoria global que se va a adjuntar a `CSharedFile`.

*bAllowGrow*<br/>
Especifica si se permite que el bloque de memoria crezca.

### <a name="remarks"></a>Comentarios

Si *bAllowGrow* es distinto de cero, el tamaño del bloque de memoria aumenta según sea necesario, por ejemplo, si intenta escribir más bytes en el archivo que el tamaño del bloque de memoria.

## <a name="see-also"></a>Vea también

[CMemFile (clase)](../../mfc/reference/cmemfile-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CMemFile (clase)](../../mfc/reference/cmemfile-class.md)
