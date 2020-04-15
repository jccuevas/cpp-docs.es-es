---
title: CAtlFileMappingBase (clase)
ms.date: 11/04/2016
f1_keywords:
- CAtlFileMappingBase
- ATLFILE/ATL::CAtlFileMappingBase
- ATLFILE/ATL::CAtlFileMappingBase::CAtlFileMappingBase
- ATLFILE/ATL::CAtlFileMappingBase::CopyFrom
- ATLFILE/ATL::CAtlFileMappingBase::GetData
- ATLFILE/ATL::CAtlFileMappingBase::GetHandle
- ATLFILE/ATL::CAtlFileMappingBase::GetMappingSize
- ATLFILE/ATL::CAtlFileMappingBase::MapFile
- ATLFILE/ATL::CAtlFileMappingBase::MapSharedMem
- ATLFILE/ATL::CAtlFileMappingBase::OpenMapping
- ATLFILE/ATL::CAtlFileMappingBase::Unmap
helpviewer_keywords:
- CAtlFileMappingBase class
ms.assetid: be555723-2790-4f57-a8fb-be4d68460775
ms.openlocfilehash: ae790cf1248c78ff9aa70c0e586f86af6c8f3b9a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318939"
---
# <a name="catlfilemappingbase-class"></a>CAtlFileMappingBase (clase)

Esta clase representa un archivo asignado a memoria.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
class CAtlFileMappingBase
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAtlFileMappingBase::CAtlFileMappingBase](#catlfilemappingbase)|El constructor.|
|[CAtlFileMappingBase::-CAtlFileMappingBase](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAtlFileMappingBase::CopyFrom](#copyfrom)|Llame a este método para copiar desde un objeto de asignación de archivos.|
|[CAtlFileMappingBase::GetData](#getdata)|Llame a este método para obtener los datos de un objeto de asignación de archivos.|
|[CAtlFileMappingBase::GetHandle](#gethandle)|Llame a este método para devolver el identificador de archivo.|
|[CAtlFileMappingBase::GetMappingSize](#getmappingsize)|Llame a este método para obtener el tamaño de asignación de un objeto de asignación de archivos.|
|[CAtlFileMappingBase::MapFile](#mapfile)|Llame a este método para crear un objeto de asignación de archivos.|
|[CAtlFileMappingBase::MapSharedMem](#mapsharedmem)|Llame a este método para crear un objeto de asignación de archivos que permita el acceso completo a todos los procesos.|
|[CAtlFileMappingBase::OpenMapping](#openmapping)|Llame a este método para devolver un identificador al objeto de asignación de archivos.|
|[CAtlFileMappingBase::Unmap](#unmap)|Llame a este método para desasignar un objeto de asignación de archivos.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAtlFileMappingBase::operator ?](#operator_eq)|Establece el objeto de asignación de archivos actual en otro objeto de asignación de archivos.|

## <a name="remarks"></a>Observaciones

La asignación de archivos es la asociación del contenido de un archivo con una parte del espacio de direcciones virtuales de un proceso. Esta clase proporciona métodos para crear objetos de asignación de archivos que permiten a los programas acceder fácilmente y compartir datos.

Para obtener más información, consulte [Asignación](/windows/win32/Memory/file-mapping) de archivos en el Windows SDK.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlfile.h

## <a name="catlfilemappingbasecatlfilemappingbase"></a><a name="catlfilemappingbase"></a>CAtlFileMappingBase::CAtlFileMappingBase

El constructor.

```
CAtlFileMappingBase(CAtlFileMappingBase& orig);
CAtlFileMappingBase() throw();
```

### <a name="parameters"></a>Parámetros

*Orig*<br/>
Objeto de asignación de archivos original que se va a copiar para crear el nuevo objeto.

### <a name="remarks"></a>Observaciones

Crea un nuevo objeto de asignación de archivos, opcionalmente mediante un objeto existente. Todavía es necesario llamar a [CAtlFileMappingBase::MapFile](#mapfile) para abrir o crear el objeto de asignación de archivos para un archivo determinado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#71](../../atl/codesnippet/cpp/catlfilemappingbase-class_1.cpp)]

## <a name="catlfilemappingbasecatlfilemappingbase"></a><a name="dtor"></a>CAtlFileMappingBase::-CAtlFileMappingBase

Destructor.

```
~CAtlFileMappingBase() throw();
```

### <a name="remarks"></a>Observaciones

Libera los recursos asignados por la clase y llama a la [CAtlFileMappingBase::Unmap](#unmap) método.

## <a name="catlfilemappingbasecopyfrom"></a><a name="copyfrom"></a>CAtlFileMappingBase::CopyFrom

Llame a este método para copiar desde un objeto de asignación de archivos.

```
HRESULT CopyFrom(CAtlFileMappingBase& orig) throw();
```

### <a name="parameters"></a>Parámetros

*Orig*<br/>
El objeto de asignación de archivos original desde el que se va a copiar.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

## <a name="catlfilemappingbasegetdata"></a><a name="getdata"></a>CAtlFileMappingBase::GetData

Llame a este método para obtener los datos de un objeto de asignación de archivos.

```
void* GetData() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero a los datos.

## <a name="catlfilemappingbasegethandle"></a><a name="gethandle"></a>CAtlFileMappingBase::GetHandle

Llame a este método para devolver un identificador al objeto de asignación de archivos.

```
HANDLE GetHandle() throw ();
```

### <a name="return-value"></a>Valor devuelto

Devuelve un identificador al objeto de asignación de archivos.

## <a name="catlfilemappingbasegetmappingsize"></a><a name="getmappingsize"></a>CAtlFileMappingBase::GetMappingSize

Llame a este método para obtener el tamaño de asignación de un objeto de asignación de archivos.

```
SIZE_T GetMappingSize() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el tamaño de asignación.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CAtlFileMappingBase::CAtlFileMappingBase](#catlfilemappingbase).

## <a name="catlfilemappingbasemapfile"></a><a name="mapfile"></a>CAtlFileMappingBase::MapFile

Llame a este método para abrir o crear un objeto de asignación de archivos para el archivo especificado.

```
HRESULT MapFile(
    HANDLE hFile,
    SIZE_T nMappingSize = 0,
    ULONGLONG nOffset = 0,
    DWORD dwMappingProtection = PAGE_READONLY,
    DWORD dwViewDesiredAccess = FILE_MAP_READ) throw();
```

### <a name="parameters"></a>Parámetros

*hArchivo*<br/>
Controlar el archivo desde el que se va a crear un objeto de asignación. *hFile* debe ser válido y no se puede establecer en INVALID_HANDLE_VALUE.

*nMappingSize*<br/>
El tamaño de la asignación. Si es 0, el tamaño máximo del objeto de asignación de archivos es igual al tamaño actual del archivo identificado por *hFile.*

*nOffset*<br/>
Desplazamiento de archivo donde debe comenzar la asignación. El valor de desplazamiento debe ser un múltiplo de la granularidad de asignación de memoria del sistema.

*dwMappingProtection*<br/>
La protección deseada para la vista de archivo cuando se asigna el archivo. Consulte *flProtect* en [CreateFileMapping](/windows/win32/api/winbase/nf-winbase-createfilemappinga) en el Windows SDK.

*dwViewDesiredAccess*<br/>
Especifica el tipo de acceso a la vista de archivo y, por lo tanto, la protección de las páginas asignadas por el archivo. Consulte *dwDesiredAccess* en [MapViewOfFileEx](/windows/win32/api/memoryapi/nf-memoryapi-mapviewoffileex) en el Windows SDK.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Una vez creado un objeto de asignación de archivos, el tamaño del archivo no debe superar el tamaño del objeto de asignación de archivos; si lo hace, no todo el contenido del archivo estará disponible para compartir. Para obtener más información, vea [CreateFileMapping](/windows/win32/api/winbase/nf-winbase-createfilemappinga) y [MapViewOfFileEx](/windows/win32/api/memoryapi/nf-memoryapi-mapviewoffileex) en el Windows SDK.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CAtlFileMappingBase::CAtlFileMappingBase](#catlfilemappingbase).

## <a name="catlfilemappingbasemapsharedmem"></a><a name="mapsharedmem"></a>CAtlFileMappingBase::MapSharedMem

Llame a este método para crear un objeto de asignación de archivos que permita el acceso completo a todos los procesos.

```
HRESULT MapSharedMem(
    SIZE_T nMappingSize,
    LPCTSTR szName,
    BOOL* pbAlreadyExisted = NULL,
    LPSECURITY_ATTRIBUTES lpsa = NULL,
    DWORD dwMappingProtection = PAGE_READWRITE,
    DWORD dwViewDesiredAccess = FILE_MAP_ALL_ACCESS) throw();
```

### <a name="parameters"></a>Parámetros

*nMappingSize*<br/>
El tamaño de la asignación. Si es 0, el tamaño máximo del objeto de asignación de archivos es igual al tamaño actual del objeto de asignación de archivos identificado por *szName*.

*szName*<br/>
El nombre del objeto de asignación.

*pbAlreadyExisted*<br/>
Apunta a un valor BOOL que se establece en TRUE si el objeto de asignación ya existía.

*lpsa*<br/>
Puntero a `SECURITY_ATTRIBUTES` una estructura que determina si los procesos secundarios pueden heredar el identificador devuelto. Consulte *lpAttributes* en [CreateFileMapping](/windows/win32/api/winbase/nf-winbase-createfilemappinga) en el Windows SDK.

*dwMappingProtection*<br/>
La protección deseada para la vista de archivo, cuando se asigna el archivo. Consulte *flProtect* en `CreateFileMapping` el Windows SDK.

*dwViewDesiredAccess*<br/>
Especifica el tipo de acceso a la vista de archivo y, por lo tanto, la protección de las páginas asignadas por el archivo. Consulte *dwDesiredAccess* en [MapViewOfFileEx](/windows/win32/api/memoryapi/nf-memoryapi-mapviewoffileex) en el Windows SDK.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

`MapShareMem`permite que un objeto de asignación de archivos existente, creado por [CreateFileMapping](/windows/win32/api/winbase/nf-winbase-createfilemappinga), se comparta entre procesos.

## <a name="catlfilemappingbaseopenmapping"></a><a name="openmapping"></a>CAtlFileMappingBase::OpenMapping

Llame a este método para abrir un objeto de asignación de archivos con nombre para el archivo especificado.

```
HRESULT OpenMapping(
    LPCTSTR szName,
    SIZE_T nMappingSize,
    ULONGLONG nOffset = 0,
    DWORD dwViewDesiredAccess = FILE_MAP_ALL_ACCESS) throw();
```

### <a name="parameters"></a>Parámetros

*szName*<br/>
El nombre del objeto de asignación. Si hay un identificador abierto para un objeto de asignación de archivos con este nombre y el descriptor de seguridad en el objeto de asignación no entra en conflicto con el parámetro *dwViewDesiredAccess,* la operación abierta se realiza correctamente.

*nMappingSize*<br/>
El tamaño de la asignación. Si es 0, el tamaño máximo del objeto de asignación de archivos es igual al tamaño actual del objeto de asignación de archivos identificado por *szName*.

*nOffset*<br/>
Desplazamiento de archivo donde debe comenzar la asignación. El valor de desplazamiento debe ser un múltiplo de la granularidad de asignación de memoria del sistema.

*dwViewDesiredAccess*<br/>
Especifica el tipo de acceso a la vista de archivo y, por lo tanto, la protección de las páginas asignadas por el archivo. Consulte *dwDesiredAccess* en [MapViewOfFileEx](/windows/win32/api/memoryapi/nf-memoryapi-mapviewoffileex) en el Windows SDK.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

En compilaciones de depuración, se producirá un error de aserción si los parámetros de entrada no son válidos.

## <a name="catlfilemappingbaseoperator-"></a><a name="operator_eq"></a>CAtlFileMappingBase::operator ?

Establece el objeto de asignación de archivos actual en otro objeto de asignación de archivos.

```
CAtlFileMappingBase& operator=(CAtlFileMappingBase& orig);
```

### <a name="parameters"></a>Parámetros

*Orig*<br/>
El objeto de asignación de archivos actual.

### <a name="return-value"></a>Valor devuelto

Devuelve una referencia al objeto actual.

## <a name="catlfilemappingbaseunmap"></a><a name="unmap"></a>CAtlFileMappingBase::Unmap

Llame a este método para desasignar un objeto de asignación de archivos.

```
HRESULT Unmap() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Consulte [UnmapViewOfFile](/windows/win32/api/memoryapi/nf-memoryapi-unmapviewoffile) en el Windows SDK para obtener más detalles.

## <a name="see-also"></a>Consulte también

[CAtlFileMapping Clase](../../atl/reference/catlfilemapping-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
