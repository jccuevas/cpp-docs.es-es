---
title: CAtlFileMappingBase (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CAtlFileMappingBase class
ms.assetid: be555723-2790-4f57-a8fb-be4d68460775
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cfc59e4652c7c758e7fb5b3ee8a228963a6b6f7d
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2018
ms.locfileid: "37883250"
---
# <a name="catlfilemappingbase-class"></a>CAtlFileMappingBase (clase)
Esta clase representa un archivo asignado a memoria.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class CAtlFileMappingBase
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAtlFileMappingBase::CAtlFileMappingBase](#catlfilemappingbase)|El constructor.|  
|[CAtlFileMappingBase:: ~ CAtlFileMappingBase](#dtor)|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAtlFileMappingBase::CopyFrom](#copyfrom)|Llame a este método para copiar desde un objeto de asignación de archivos.|  
|[CAtlFileMappingBase::GetData](#getdata)|Llame a este método para obtener los datos de un objeto de asignación de archivos.|  
|[CAtlFileMappingBase::GetHandle](#gethandle)|Llame a este método para devolver el identificador de archivo.|  
|[CAtlFileMappingBase::GetMappingSize](#getmappingsize)|Llame a este método para obtener el tamaño de asignación de un objeto de asignación de archivos.|  
|[CAtlFileMappingBase::MapFile](#mapfile)|Llame a este método para crear un objeto de asignación de archivos.|  
|[CAtlFileMappingBase::MapSharedMem](#mapsharedmem)|Llame a este método para crear un objeto de asignación de archivos que permite el acceso completo a todos los procesos.|  
|[CAtlFileMappingBase::OpenMapping](#openmapping)|Llame a este método para devolver un identificador para el objeto de asignación de archivos.|  
|[CAtlFileMappingBase::Unmap](#unmap)|Llame a este método para anular la asignación de un objeto de asignación de archivos.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAtlFileMappingBase::operator =](#operator_eq)|Establece el objeto de asignación de archivos actual a otro objeto de asignación de archivos.|  
  
## <a name="remarks"></a>Comentarios  
 Asignación de archivos es la asociación de contenido de un archivo con una parte del espacio de direcciones virtuales de un proceso. Esta clase proporciona métodos para crear los objetos de asignación de archivos que permiten programas para tener acceso fácilmente a y compartir datos.  
  
 Para obtener más información, consulte [asignación de archivos](http://msdn.microsoft.com/library/windows/desktop/aa366556) en el SDK de Windows.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlfile.h  
  
##  <a name="catlfilemappingbase"></a>  CAtlFileMappingBase::CAtlFileMappingBase  
 El constructor.  
  
```
CAtlFileMappingBase(CAtlFileMappingBase& orig);  
CAtlFileMappingBase() throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *orig.*  
 El objeto de asignación del archivo original a copiar para crear el nuevo objeto.  
  
### <a name="remarks"></a>Comentarios  
 Crea un nuevo objeto de asignación de archivos, utilizando opcionalmente un objeto existente. Sigue siendo necesario llamar a [CAtlFileMappingBase::MapFile](#mapfile) abrir o crear el objeto de asignación de archivos de un archivo determinado.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities#71](../../atl/codesnippet/cpp/catlfilemappingbase-class_1.cpp)]  
  
##  <a name="dtor"></a>  CAtlFileMappingBase:: ~ CAtlFileMappingBase  
 Destructor.  
  
```
~CAtlFileMappingBase() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Libera todos los recursos asignados por la clase y llama a la [CAtlFileMappingBase::Unmap](#unmap) método.  
  
##  <a name="copyfrom"></a>  CAtlFileMappingBase::CopyFrom  
 Llame a este método para copiar desde un objeto de asignación de archivos.  
  
```
HRESULT CopyFrom(CAtlFileMappingBase& orig) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *orig.*  
 El objeto de asignación de archivos original para copiarlos.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.  
  
##  <a name="getdata"></a>  CAtlFileMappingBase::GetData  
 Llame a este método para obtener los datos de un objeto de asignación de archivos.  
  
```
void* GetData() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un puntero a los datos.  
  
##  <a name="gethandle"></a>  CAtlFileMappingBase::GetHandle  
 Llame a este método para devolver un identificador para el objeto de asignación de archivos.  
  
```
HANDLE GetHandle() throw ();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un identificador para el objeto de asignación de archivos.  
  
##  <a name="getmappingsize"></a>  CAtlFileMappingBase::GetMappingSize  
 Llame a este método para obtener el tamaño de asignación de un objeto de asignación de archivos.  
  
```
SIZE_T GetMappingSize() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el tamaño de asignación.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CAtlFileMappingBase::CAtlFileMappingBase](#catlfilemappingbase).  
  
##  <a name="mapfile"></a>  CAtlFileMappingBase::MapFile  
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
 *hFile*  
 Handle para el archivo desde el que se va a crear un objeto de asignación. *hFile* debe ser válido y no puede establecerse en INVALID_HANDLE_VALUE.  
  
 *nMappingSize*  
 El tamaño de asignación. Si es 0, el tamaño máximo del archivo de asignación objeto es igual al tamaño actual del archivo identificado por *hFile.*  
  
 *nOffset*  
 El desplazamiento de archivo donde asignación se va a comenzar. El valor de desplazamiento debe ser un múltiplo de granularidad de asignación de memoria del sistema.  
  
 *dwMappingProtection*  
 La protección que desea para la vista del archivo cuando se asigna el archivo. Consulte *flProtect* en [CreateFileMapping](http://msdn.microsoft.com/library/windows/desktop/aa366537) en el SDK de Windows.  
  
 *dwViewDesiredAccess*  
 Especifica el tipo de acceso a la vista del archivo y, por lo tanto, la protección de las páginas asignadas por el archivo. Consulte *dwDesiredAccess* en [MapViewOfFileEx](http://msdn.microsoft.com/library/windows/desktop/aa366763) en el SDK de Windows.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Una vez creado un objeto de asignación de archivos, el tamaño del archivo no puede superar el tamaño del objeto de asignación de archivos; Si es así, no todos el contenido del archivo estará disponibles para uso compartido. Para obtener más información, consulte [CreateFileMapping](http://msdn.microsoft.com/library/windows/desktop/aa366537) y [MapViewOfFileEx](http://msdn.microsoft.com/library/windows/desktop/aa366763) en el SDK de Windows.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CAtlFileMappingBase::CAtlFileMappingBase](#catlfilemappingbase).  
  
##  <a name="mapsharedmem"></a>  CAtlFileMappingBase::MapSharedMem  
 Llame a este método para crear un objeto de asignación de archivos que permite el acceso completo a todos los procesos.  
  
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
 *nMappingSize*  
 El tamaño de asignación. Si es 0, el tamaño máximo del archivo de asignación objeto es igual al tamaño actual del objeto de asignación del archivo identificado por *szName*.  
  
 *szName*  
 El nombre del objeto de asignación.  
  
 *pbAlreadyExisted*  
 Apunta a un valor booleano que se establece en TRUE si el objeto de asignación ya existía.  
  
 *LPSA*  
 El puntero a un `SECURITY_ATTRIBUTES` estructura que determina si el identificador devuelto se puede heredar mediante procesos secundarios. Consulte *lpAttributes* en [CreateFileMapping](http://msdn.microsoft.com/library/windows/desktop/aa366537) en el SDK de Windows.  
  
 *dwMappingProtection*  
 La protección que desea para la vista del archivo, cuando se asigna el archivo. Consulte *flProtect* en `CreateFileMapping` en el SDK de Windows.  
  
 *dwViewDesiredAccess*  
 Especifica el tipo de acceso a la vista del archivo y, por lo tanto, la protección de las páginas asignadas por el archivo. Consulte *dwDesiredAccess* en [MapViewOfFileEx](http://msdn.microsoft.com/library/windows/desktop/aa366763) en el SDK de Windows.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 `MapShareMem` permite que un objeto de asignación de archivos existente, creado por [CreateFileMapping](http://msdn.microsoft.com/library/windows/desktop/aa366537)para compartirse entre los procesos.  
  
##  <a name="openmapping"></a>  CAtlFileMappingBase::OpenMapping  
 Llame a este método para abrir un objeto de asignación de archivos con nombre para el archivo especificado.  
  
```
HRESULT OpenMapping(
    LPCTSTR szName,
    SIZE_T nMappingSize,
    ULONGLONG nOffset = 0,
    DWORD dwViewDesiredAccess = FILE_MAP_ALL_ACCESS) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *szName*  
 El nombre del objeto de asignación. Si hay un identificador abierto a un objeto de asignación de archivos con este nombre y el descriptor de seguridad en el objeto de asignación no entra en conflicto con el *dwViewDesiredAccess* la operación de apertura de parámetro, se realiza correctamente.  
  
 *nMappingSize*  
 El tamaño de asignación. Si es 0, el tamaño máximo del archivo de asignación objeto es igual al tamaño actual del objeto de asignación del archivo identificado por *szName*.  
  
 *nOffset*  
 El desplazamiento de archivo donde asignación se va a comenzar. El valor de desplazamiento debe ser un múltiplo de granularidad de asignación de memoria del sistema.  
  
 *dwViewDesiredAccess*  
 Especifica el tipo de acceso a la vista del archivo y, por lo tanto, la protección de las páginas asignadas por el archivo. Consulte *dwDesiredAccess* en [MapViewOfFileEx](http://msdn.microsoft.com/library/windows/desktop/aa366763) en el SDK de Windows.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 En las compilaciones de depuración, se producirá un error de aserción si los parámetros de entrada no son válidos.  
  
##  <a name="operator_eq"></a>  CAtlFileMappingBase::operator =  
 Establece el objeto de asignación de archivos actual a otro objeto de asignación de archivos.  
  
```
CAtlFileMappingBase& operator=(CAtlFileMappingBase& orig);
```  
  
### <a name="parameters"></a>Parámetros  
 *orig.*  
 El objeto de asignación de archivos actual.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve una referencia al objeto actual.  
  
##  <a name="unmap"></a>  CAtlFileMappingBase::Unmap  
 Llame a este método para anular la asignación de un objeto de asignación de archivos.  
  
```
HRESULT Unmap() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Consulte [UnmapViewOfFile](http://msdn.microsoft.com/library/windows/desktop/aa366882) en el SDK de Windows para obtener más detalles.  
  
## <a name="see-also"></a>Vea también  
 [CAtlFileMapping (clase)](../../atl/reference/catlfilemapping-class.md)   
 [Información general de clases](../../atl/atl-class-overview.md)
