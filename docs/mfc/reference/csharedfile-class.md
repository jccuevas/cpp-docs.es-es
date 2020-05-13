---
title: CSharedFile (clase)
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
ms.openlocfilehash: c715ca1b8a2b647f89ada008f3c6606ca5e58783
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750394"
---
# <a name="csharedfile-class"></a>CSharedFile (clase)

La clase derivada [de CMemFile](../../mfc/reference/cmemfile-class.md)que admite archivos de memoria compartida.

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

## <a name="remarks"></a>Observaciones

Los archivos de memoria se comportan como archivos de disco. La diferencia es que un archivo de memoria se almacena en RAM en lugar de en el disco. Un archivo de memoria es útil para el almacenamiento temporal rápido o para transferir bytes sin procesar u objetos serializados entre procesos independientes.

Los archivos de memoria compartida difieren de otros archivos de memoria en que la memoria para ellos se asigna con la función [GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc) de Windows. La `CSharedFile` clase almacena datos en un bloque `GlobalAlloc`de memoria asignado globalmente (creado mediante ), y este bloque de memoria se `IDataObject`puede compartir mediante DDE, el Portapapeles u otras operaciones de transferencia de datos uniformes OLE/COM, por ejemplo, mediante .

`GlobalAlloc`devuelve un identificador HGLOBAL en lugar de un puntero a la memoria, como el puntero devuelto por [malloc](../../c-runtime-library/reference/malloc.md). El mango HGLOBAL es necesario en ciertas aplicaciones. Por ejemplo, para colocar datos en el Portapapeles necesita un identificador HGLOBAL.

`CSharedFile`no utiliza archivos asignados a memoria y los datos no se pueden compartir directamente entre procesos.

`CSharedFile`objetos pueden asignar automáticamente su propia memoria. O bien, puede adjuntar su `CSharedFile` propio bloque de memoria al objeto llamando a [CSharedFile::SetHandle](#sethandle). En cualquier caso, la memoria para aumentar `nGrowBytes`el archivo `nGrowBytes` de memoria automáticamente se asigna en incrementos de tamaño si no es cero.

Para obtener más información, vea el artículo [Archivos en MFC](../../mfc/files-in-mfc.md) y [Control](../../c-runtime-library/file-handling.md) de archivos en la Referencia de biblioteca en tiempo *de ejecución*.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[CMemFile](../../mfc/reference/cmemfile-class.md)

`CSharedFile`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxadv.h

## <a name="csharedfilecsharedfile"></a><a name="csharedfile"></a>CSharedFile::CSharedFile

Construye un `CSharedFile` objeto y asigna memoria para él.

```
CSharedFile(
    UINT nAllocFlags = GMEM_DDESHARE | GMEM_MOVEABLE,
    UINT nGrowBytes = 4096);
```

### <a name="parameters"></a>Parámetros

*nAllocFlags*<br/>
Indicadores que indican cómo se va a asignar la memoria. Consulte [GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc) para obtener una lista de valores de marca válidos.

*nGrowBytes*<br/>
El incremento de asignación de memoria en bytes.

## <a name="csharedfiledetach"></a><a name="detach"></a>CSharedFile::Detach

Llame a esta función para cerrar el archivo de memoria y separarlo del bloque de memoria.

```
HGLOBAL Detach();
```

### <a name="return-value"></a>Valor devuelto

Identificador del bloque de memoria que contiene el contenido del archivo de memoria.

### <a name="remarks"></a>Observaciones

Puede volver a abrirlo llamando a [SetHandle](#sethandle), mediante el identificador devuelto por **Detach**.

## <a name="csharedfilesethandle"></a><a name="sethandle"></a>CSharedFile::SetHandle

Llame a esta función para asociar `CSharedFile` un bloque de memoria global al objeto.

```cpp
void SetHandle(
    HGLOBAL hGlobalMemory,
    BOOL bAllowGrow = TRUE);
```

### <a name="parameters"></a>Parámetros

*hGlobalMemory*<br/>
Controle la memoria global que `CSharedFile`se va a adjuntar a la .

*bAllowGrow*<br/>
Especifica si el bloque de memoria puede crecer.

### <a name="remarks"></a>Observaciones

Si *bAllowGrow* es distinto de cero, el tamaño del bloque de memoria aumenta según sea necesario, por ejemplo, si intenta escribir más bytes en el archivo que el tamaño del bloque de memoria.

## <a name="see-also"></a>Vea también

[Clase CMemFile](../../mfc/reference/cmemfile-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clase CMemFile](../../mfc/reference/cmemfile-class.md)
