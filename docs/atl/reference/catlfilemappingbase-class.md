---
title: Clase CAtlFileMappingBase | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
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
caps.latest.revision: 20
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
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: 439f123bc0addbbec2a26102d0197d0a1f14a8d5
ms.lasthandoff: 02/24/2017

---
# <a name="catlfilemappingbase-class"></a>Clase CAtlFileMappingBase
Esta clase representa un archivo asignado a memoria.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no pueden utilizarse en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class CAtlFileMappingBase
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAtlFileMappingBase::CAtlFileMappingBase](#catlfilemappingbase)|El constructor.|  
|[CAtlFileMappingBase:: ~ CAtlFileMappingBase](#dtor)|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAtlFileMappingBase::CopyFrom](#copyfrom)|Llamar a este método para copiar un objeto de asignación de archivos.|  
|[CAtlFileMappingBase::GetData](#getdata)|Llame a este método para obtener los datos de un objeto de asignación de archivos.|  
|[CAtlFileMappingBase::GetHandle](#gethandle)|Llame a este método para devolver el identificador de archivo.|  
|[CAtlFileMappingBase::GetMappingSize](#getmappingsize)|Llamar a este método para obtener el tamaño de la asignación de un objeto de asignación de archivos.|  
|[CAtlFileMappingBase::MapFile](#mapfile)|Llamar a este método para crear un objeto de asignación de archivos.|  
|[CAtlFileMappingBase::MapSharedMem](#mapsharedmem)|Llame a este método para crear un objeto de asignación de archivos que permite el acceso completo a todos los procesos.|  
|[CAtlFileMappingBase::OpenMapping](#openmapping)|Llamar a este método para devolver un identificador para el objeto de asignación de archivos.|  
|[CAtlFileMappingBase::Unmap](#unmap)|Llame a este método para anular la asignación de un objeto de asignación de archivos.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAtlFileMappingBase::operator =](#operator_eq)|Establece el objeto de asignación de archivos actual a otro objeto de asignación de archivos.|  
  
## <a name="remarks"></a>Comentarios  
 Asignación de archivos es la asociación del contenido de un archivo con una parte del espacio de direcciones virtuales de un proceso. Esta clase proporciona métodos para crear objetos de asignación de archivos que permiten a los programas fácilmente acceso a datos.  
  
 Para obtener más información, consulte [asignación de archivos](http://msdn.microsoft.com/library/windows/desktop/aa366556) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlfile.h  
  
##  <a name="catlfilemappingbase"></a>CAtlFileMappingBase::CAtlFileMappingBase  
 El constructor.  
  
```
CAtlFileMappingBase(CAtlFileMappingBase& orig);  
CAtlFileMappingBase() throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `orig`  
 El objeto original de asignación de archivos para copiar para crear el nuevo objeto.  
  
### <a name="remarks"></a>Comentarios  
 Crea un nuevo objeto de asignación de archivos, utilizando opcionalmente un objeto existente. Sigue siendo necesario llamar a [CAtlFileMappingBase::MapFile](#mapfile) abrir o crear el objeto de asignación de archivos para un archivo determinado.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities&#71;](../../atl/codesnippet/cpp/catlfilemappingbase-class_1.cpp)]  
  
##  <a name="dtor"></a>CAtlFileMappingBase:: ~ CAtlFileMappingBase  
 Destructor.  
  
```
~CAtlFileMappingBase() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Libera todos los recursos asignados por la clase y llama el [CAtlFileMappingBase::Unmap](#unmap) método.  
  
##  <a name="copyfrom"></a>CAtlFileMappingBase::CopyFrom  
 Llamar a este método para copiar un objeto de asignación de archivos.  
  
```
HRESULT CopyFrom(CAtlFileMappingBase& orig) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `orig`  
 El objeto de asignación de archivos original para copiar desde.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK` éxito o error `HRESULT` en caso de error.  
  
##  <a name="getdata"></a>CAtlFileMappingBase::GetData  
 Llame a este método para obtener los datos de un objeto de asignación de archivos.  
  
```
void* GetData() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un puntero a los datos.  
  
##  <a name="gethandle"></a>CAtlFileMappingBase::GetHandle  
 Llamar a este método para devolver un identificador para el objeto de asignación de archivos.  
  
```
HANDLE GetHandle() throw ();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un identificador para el objeto de asignación de archivos.  
  
##  <a name="getmappingsize"></a>CAtlFileMappingBase::GetMappingSize  
 Llamar a este método para obtener el tamaño de la asignación de un objeto de asignación de archivos.  
  
```
SIZE_T GetMappingSize() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el tamaño de asignación.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CAtlFileMappingBase::CAtlFileMappingBase](#catlfilemappingbase).  
  
##  <a name="mapfile"></a>CAtlFileMappingBase::MapFile  
 Llamar a este método para abrir o crear un objeto de asignación de archivos para el archivo especificado.  
  
```
HRESULT MapFile(
    HANDLE hFile,
    SIZE_T nMappingSize = 0,
    ULONGLONG nOffset = 0,
    DWORD dwMappingProtection = PAGE_READONLY,
    DWORD dwViewDesiredAccess = FILE_MAP_READ) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `hFile`  
 Identificador para el archivo desde el que se va a crear un objeto de asignación. `hFile`debe ser válido y no puede establecerse en INVALID_HANDLE_VALUE.  
  
 `nMappingSize`  
 El tamaño de asignación. Si es 0, el tamaño máximo del objeto de asignación de archivos es igual que el tamaño actual del archivo identificado por *hFile.*  
  
 `nOffset`  
 El desplazamiento de archivo donde asignación se va a comenzar. El valor de desplazamiento debe ser un múltiplo de granularidad de asignación de memoria del sistema.  
  
 `dwMappingProtection`  
 La protección que desea para la vista de archivo cuando se asigna el archivo. Consulte `flProtect` en [CreateFileMapping](http://msdn.microsoft.com/library/windows/desktop/aa366537) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 `dwViewDesiredAccess`  
 Especifica el tipo de acceso a la vista de archivo y, por lo tanto, la protección de las páginas asignadas por el archivo. Consulte `dwDesiredAccess` en [MapViewOfFileEx](http://msdn.microsoft.com/library/windows/desktop/aa366763) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK` éxito o error `HRESULT` en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Después de crear un objeto de asignación de archivos, el tamaño del archivo no debe superar el tamaño del objeto de asignación de archivos; Si lo hace, no todos el contenido del archivo estará disponibles para compartir. Para obtener más información, consulte [CreateFileMapping](http://msdn.microsoft.com/library/windows/desktop/aa366537) y [MapViewOfFileEx](http://msdn.microsoft.com/library/windows/desktop/aa366763) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CAtlFileMappingBase::CAtlFileMappingBase](#catlfilemappingbase).  
  
##  <a name="mapsharedmem"></a>CAtlFileMappingBase::MapSharedMem  
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
 `nMappingSize`  
 El tamaño de asignación. Si es 0, el tamaño máximo del objeto de asignación de archivos es igual que el tamaño actual del objeto de asignación del archivo identificado por`szName.`  
  
 `szName`  
 El nombre del objeto de asignación.  
  
 *pbAlreadyExisted*  
 Señala a un valor booleano que se establece en TRUE si el objeto de asignación ya existía.  
  
 `lpsa`  
 El puntero a un **SECURITY_ATTRIBUTES** estructura que determina si los procesos secundarios puede heredar el identificador devuelto. Consulte *lpAttributes* en [CreateFileMapping](http://msdn.microsoft.com/library/windows/desktop/aa366537) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 `dwMappingProtection`  
 La protección que desea para la vista de archivo, cuando se asigna el archivo. Consulte `flProtect` en **CreateFileMapping** en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 `dwViewDesiredAccess`  
 Especifica el tipo de acceso a la vista de archivo y, por lo tanto, la protección de las páginas asignadas por el archivo. Consulte `dwDesiredAccess` en [MapViewOfFileEx](http://msdn.microsoft.com/library/windows/desktop/aa366763) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK` éxito o error `HRESULT` en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 **MapShareMem** permite que un objeto de asignación de archivos existente, creado por [CreateFileMapping](http://msdn.microsoft.com/library/windows/desktop/aa366537), compartir entre procesos.  
  
##  <a name="openmapping"></a>CAtlFileMappingBase::OpenMapping  
 Llamar a este método para abrir un objeto de asignación de archivos con nombre para el archivo especificado.  
  
```
HRESULT OpenMapping(
    LPCTSTR szName,
    SIZE_T nMappingSize,
    ULONGLONG nOffset = 0,
    DWORD dwViewDesiredAccess = FILE_MAP_ALL_ACCESS) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `szName`  
 El nombre del objeto de asignación. Si hay un identificador abierto a un objeto de asignación de archivos con este nombre y el descriptor de seguridad en el objeto de asignación no entra en conflicto con el `dwViewDesiredAccess` la operación de apertura de parámetro, se realiza correctamente.  
  
 `nMappingSize`  
 El tamaño de asignación. Si es 0, el tamaño máximo del objeto de asignación de archivos es igual que el tamaño actual del objeto de asignación del archivo identificado por`szName.`  
  
 `nOffset`  
 El desplazamiento de archivo donde asignación se va a comenzar. El valor de desplazamiento debe ser un múltiplo de granularidad de asignación de memoria del sistema.  
  
 `dwViewDesiredAccess`  
 Especifica el tipo de acceso a la vista de archivo y, por lo tanto, la protección de las páginas asignadas por el archivo. Consulte `dwDesiredAccess` en [MapViewOfFileEx](http://msdn.microsoft.com/library/windows/desktop/aa366763) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK` éxito o error `HRESULT` en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 En compilaciones de depuración, se producirá un error de aserción si los parámetros de entrada no son válidos.  
  
##  <a name="operator_eq"></a>CAtlFileMappingBase::operator =  
 Establece el objeto de asignación de archivos actual a otro objeto de asignación de archivos.  
  
```
CAtlFileMappingBase& operator=(CAtlFileMappingBase& orig);
```  
  
### <a name="parameters"></a>Parámetros  
 `orig`  
 El objeto de asignación de archivos actual.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve una referencia al objeto actual.  
  
##  <a name="unmap"></a>CAtlFileMappingBase::Unmap  
 Llame a este método para anular la asignación de un objeto de asignación de archivos.  
  
```
HRESULT Unmap() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK` éxito o error `HRESULT` en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Consulte [UnmapViewOfFile](http://msdn.microsoft.com/library/windows/desktop/aa366882) en la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] para obtener más detalles.  
  
## <a name="see-also"></a>Vea también  
 [Clase CAtlFileMapping](../../atl/reference/catlfilemapping-class.md)   
 [Información general de la clase](../../atl/atl-class-overview.md)

