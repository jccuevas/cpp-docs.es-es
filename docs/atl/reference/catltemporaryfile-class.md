---
title: Clase CAtlTemporaryFile | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAtlTemporaryFile
- ATLFILE/ATL::CAtlTemporaryFile
- ATLFILE/ATL::CAtlTemporaryFile::CAtlTemporaryFile
- ATLFILE/ATL::CAtlTemporaryFile::Close
- ATLFILE/ATL::CAtlTemporaryFile::Create
- ATLFILE/ATL::CAtlTemporaryFile::Flush
- ATLFILE/ATL::CAtlTemporaryFile::GetPosition
- ATLFILE/ATL::CAtlTemporaryFile::GetSize
- ATLFILE/ATL::CAtlTemporaryFile::HandsOff
- ATLFILE/ATL::CAtlTemporaryFile::HandsOn
- ATLFILE/ATL::CAtlTemporaryFile::LockRange
- ATLFILE/ATL::CAtlTemporaryFile::Read
- ATLFILE/ATL::CAtlTemporaryFile::Seek
- ATLFILE/ATL::CAtlTemporaryFile::SetSize
- ATLFILE/ATL::CAtlTemporaryFile::TempFileName
- ATLFILE/ATL::CAtlTemporaryFile::UnlockRange
- ATLFILE/ATL::CAtlTemporaryFile::Write
dev_langs:
- C++
helpviewer_keywords:
- CAtlTemporaryFile class
ms.assetid: 05f0f2a5-94f6-4594-8dae-b114292ff5f9
caps.latest.revision: 18
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 9673c5a137feddb0eb696945ec6abeb5f3cb062e
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="catltemporaryfile-class"></a>Clase CAtlTemporaryFile
Esta clase proporciona métodos para la creación y uso de un archivo temporal.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no pueden utilizarse en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class CAtlTemporaryFile
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile)|El constructor.|  
|[CAtlTemporaryFile:: ~ CAtlTemporaryFile](#dtor)|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAtlTemporaryFile::Close](#close)|Llamar a este método para cerrar un archivo temporal y elimine su contenido o almacenarlos en el nombre de archivo especificado.|  
|[CAtlTemporaryFile::Create](#create)|Llame a este método para crear un archivo temporal.|  
|[CAtlTemporaryFile::Flush](#flush)|Llamar a este método para obligar a todos los datos permanecen en el búfer de archivo se escriban en el archivo temporal.|  
|[CAtlTemporaryFile::GetPosition](#getposition)|Llame a este método para obtener la posición actual del puntero de archivo.|  
|[CAtlTemporaryFile::GetSize](#getsize)|Llamar a este método para obtener el tamaño en bytes del archivo temporal.|  
|[CAtlTemporaryFile::HandsOff](#handsoff)|Llamar a este método para desasociar el archivo desde el `CAtlTemporaryFile` objeto.|  
|[CAtlTemporaryFile::HandsOn](#handson)|Llame a este método para abrir un archivo temporal existente y coloque el puntero al final del archivo.|  
|[CAtlTemporaryFile::LockRange](#lockrange)|Llame a este método para bloquear una región en el archivo para impedir que otros procesos tengan acceso a él.|  
|[CAtlTemporaryFile::Read](#read)|Llame a este método para leer los datos desde el archivo temporal en la posición indicada por el puntero de archivo.|  
|[CAtlTemporaryFile::Seek](#seek)|Llamar a este método para mover el puntero de archivo del archivo temporal.|  
|[CAtlTemporaryFile::SetSize](#setsize)|Llamar a este método para establecer el tamaño del archivo temporal.|  
|[CAtlTemporaryFile::TempFileName](#tempfilename)|Llame a este método para devolver el nombre del archivo temporal.|  
|[CAtlTemporaryFile::UnlockRange](#unlockrange)|Llamar a este método para desbloquear una región del archivo temporal.|  
|[CAtlTemporaryFile::Write](#write)|Llamar a este método para escribir datos en el archivo temporal en la posición indicada por el puntero de archivo.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[IDENTIFICADOR de CAtlTemporaryFile::operator](#operator_handle)|Devuelve un identificador para el archivo temporal.|  
  
## <a name="remarks"></a>Comentarios  
 `CAtlTemporaryFile`facilita la creación y uso de un archivo temporal. Automáticamente el archivo es denominado, abierto, cerrado y eliminado. Si el contenido del archivo es necesario después de cerrar el archivo, pueden guardar en un archivo nuevo con un nombre especificado.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlfile.h  
  
## <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).  
  
##  <a name="catltemporaryfile"></a>CAtlTemporaryFile::CAtlTemporaryFile  
 El constructor.  
  
```
CAtlTemporaryFile() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 No se abre realmente un archivo hasta que se realiza una llamada a [CAtlTemporaryFile::Create](#create).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities&#73;](../../atl/codesnippet/cpp/catltemporaryfile-class_1.cpp)]  
  
##  <a name="dtor"></a>CAtlTemporaryFile:: ~ CAtlTemporaryFile  
 Destructor.  
  
```
~CAtlTemporaryFile() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 El destructor llama [CAtlTemporaryFile::Close](#close).  
  
##  <a name="close"></a>CAtlTemporaryFile::Close  
 Llamar a este método para cerrar un archivo temporal y elimine su contenido o almacenarlos en el nombre de archivo especificado.  
  
```
HRESULT Close(LPCTSTR szNewName = NULL) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *szNewName*  
 El nombre para el nuevo archivo almacenar el contenido del archivo temporal. Si este argumento es NULL, se elimina el contenido del archivo temporal.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK` éxito o error `HRESULT` en caso de error.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).  
  
##  <a name="create"></a>CAtlTemporaryFile::Create  
 Llame a este método para crear un archivo temporal.  
  
```
HRESULT Create(LPCTSTR pszDir = NULL, DWORD dwDesiredAccess = GENERIC_WRITE) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `pszDir`  
 La ruta de acceso para el archivo temporal. Si es NULL, [GetTempPath](http://msdn.microsoft.com/library/windows/desktop/aa364992) se llamará para asignar una ruta de acceso.  
  
 `dwDesiredAccess`  
 El acceso deseado. Consulte `dwDesiredAccess` en [CreateFile](http://msdn.microsoft.com/library/windows/desktop/aa363858) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK` éxito o error `HRESULT` en caso de error.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).  
  
##  <a name="flush"></a>CAtlTemporaryFile::Flush  
 Llamar a este método para obligar a todos los datos permanecen en el búfer de archivo se escriban en el archivo temporal.  
  
```
HRESULT Flush() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK` éxito o error `HRESULT` en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Similar a [CAtlTemporaryFile::HandsOff](#handsoff), salvo que no se cierra el archivo.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).  
  
##  <a name="getposition"></a>CAtlTemporaryFile::GetPosition  
 Llame a este método para obtener la posición actual del puntero de archivo.  
  
```
HRESULT GetPosition(ULONGLONG& nPos) const throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `nPos`  
 La posición de bytes.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK` éxito o error `HRESULT` en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Para cambiar la posición del puntero de archivo, use [CAtlTemporaryFile::Seek](#seek).  
  
##  <a name="getsize"></a>CAtlTemporaryFile::GetSize  
 Llamar a este método para obtener el tamaño en bytes del archivo temporal.  
  
```
HRESULT GetSize(ULONGLONG& nLen) const throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `nLen`  
 El número de bytes en el archivo.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK` éxito o error `HRESULT` en caso de error.  
  
##  <a name="handsoff"></a>CAtlTemporaryFile::HandsOff  
 Llamar a este método para desasociar el archivo desde el `CAtlTemporaryFile` objeto.  
  
```
HRESULT HandsOff() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK` éxito o error `HRESULT` en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 `HandsOff`y [CAtlTemporaryFile::HandsOn](#handson) se utilizan para desasociar el archivo desde el objeto y acoplarlo si es necesario. `HandsOff`se forzar los datos permanecen en el búfer de archivo se escriban en el archivo temporal y, a continuación, cierre el archivo. Si desea cerrar y eliminar el archivo permanentemente, o si desea cerrar y conservar el contenido del archivo con un nombre determinado, use [CAtlTemporaryFile::Close](#close).  
  
##  <a name="handson"></a>CAtlTemporaryFile::HandsOn  
 Llame a este método para abrir un archivo temporal existente y coloque el puntero al final del archivo.  
  
```
HRESULT HandsOn() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK` éxito o error `HRESULT` en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 [CAtlTemporaryFile::HandsOff](#handsoff) y `HandsOn` se utilizan para desasociar el archivo desde el objeto y acoplarlo si es necesario.  
  
##  <a name="lockrange"></a>CAtlTemporaryFile::LockRange  
 Llame a este método para bloquear una región en el archivo temporal para impedir que otros procesos tengan acceso a él.  
  
```
HRESULT LockRange(ULONGLONG nPos, ULONGLONG nCount) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `nPos`  
 La posición del archivo donde debe comenzar el bloqueo.  
  
 `nCount`  
 La longitud del intervalo de bytes que se bloquee.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK` éxito o error `HRESULT` en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 El bloqueo de bytes en un archivo impide que otros procesos obtengan acceso a dichos bytes. Puede bloquear más de una región de un archivo, pero no las áreas superpuestas se permiten. Para desbloquear correctamente una región, utilice [CAtlTemporaryFile::UnlockRange](#unlockrange), garantizar el intervalo de bytes corresponde exactamente a la región que se ha bloqueado anteriormente. `LockRange`no combina regiones adyacentes; Si dos regiones bloqueadas son adyacentes, debe desbloquear cada uno por separado.  
  
##  <a name="operator_handle"></a>IDENTIFICADOR de CAtlTemporaryFile::operator  
 Devuelve un identificador para el archivo temporal.  
  
```  
operator HANDLE() throw();
```  
  
##  <a name="read"></a>CAtlTemporaryFile::Read  
 Llame a este método para leer los datos desde el archivo temporal en la posición indicada por el puntero de archivo.  
  
```
HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize,
    DWORD& nBytesRead) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `pBuffer`  
 Puntero al búfer que recibirá los datos leídos desde el archivo.  
  
 `nBufSize`  
 El tamaño del búfer en bytes.  
  
 `nBytesRead`  
 Número de bytes leídos.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK` éxito o error `HRESULT` en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Llamadas [CAtlFile::Read](../../atl/reference/catlfile-class.md#read). Para cambiar la posición del puntero de archivo, llame a [CAtlTemporaryFile::Seek](#seek).  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).  
  
##  <a name="seek"></a>CAtlTemporaryFile::Seek  
 Llamar a este método para mover el puntero de archivo del archivo temporal.  
  
```
HRESULT Seek(LONGLONG nOffset, DWORD dwFrom = FILE_CURRENT) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `nOffset`  
 El desplazamiento, en bytes, desde el punto inicial proporcionado por *dwFrom.*  
  
 `dwFrom`  
 El punto de partida (FILE_BEGIN, FILE_CURRENT o FILE_END).  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK` éxito o error `HRESULT` en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Llamadas [CAtlFile::Seek](../../atl/reference/catlfile-class.md#seek). Para obtener la posición del puntero de archivo actual, llame a [CAtlTemporaryFile::GetPosition](#getposition).  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).  
  
##  <a name="setsize"></a>CAtlTemporaryFile::SetSize  
 Llamar a este método para establecer el tamaño del archivo temporal.  
  
```
HRESULT SetSize(ULONGLONG nNewLen) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `nNewLen`  
 La nueva longitud del archivo en bytes.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK` éxito o error `HRESULT` en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Llamadas [CAtlFile::SetSize](../../atl/reference/catlfile-class.md#setsize). En la devolución, se sitúa el puntero de archivo al final del archivo.  
  
##  <a name="tempfilename"></a>CAtlTemporaryFile::TempFileName  
 Llame a este método para devolver el nombre del archivo temporal.  
  
```
LPCTSTR TempFileName() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el `LPCTSTR` seleccionando el nombre de archivo.  
  
### <a name="remarks"></a>Comentarios  
 El nombre de archivo se genera en [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile) con una llamada a la [GetTempFile](http://msdn.microsoft.com/library/windows/desktop/aa364991) [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] (función). La extensión de archivo será siempre "TFR" para el archivo temporal.  
  
##  <a name="unlockrange"></a>CAtlTemporaryFile::UnlockRange  
 Llamar a este método para desbloquear una región del archivo temporal.  
  
```
HRESULT UnlockRange(ULONGLONG nPos, ULONGLONG nCount) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `nPos`  
 La posición del archivo donde debe comenzar el desbloqueo.  
  
 `nCount`  
 La longitud del intervalo de bytes que se desbloquearán.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK` éxito o error `HRESULT` en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Llamadas [CAtlFile::UnlockRange](../../atl/reference/catlfile-class.md#unlockrange).  
  
##  <a name="write"></a>CAtlTemporaryFile::Write  
 Llamar a este método para escribir datos en el archivo temporal en la posición indicada por el puntero de archivo.  
  
```
HRESULT Write(  
    LPCVOID pBuffer,
    DWORD nBufSize,
    DWORD* pnBytesWritten = NULL) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `pBuffer`  
 Búfer que contiene los datos se escriban en el archivo.  
  
 `nBufSize`  
 El número de bytes que se transfieren desde el búfer.  
  
 `pnBytesWritten`  
 Número de bytes escritos.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK` éxito o error `HRESULT` en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Llamadas [CAtlFile::Write](../../atl/reference/catlfile-class.md#write).  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).  
  
## <a name="see-also"></a>Vea también  
 [Información general de la clase](../../atl/atl-class-overview.md)   
 [Clase CAtlFile](../../atl/reference/catlfile-class.md)

