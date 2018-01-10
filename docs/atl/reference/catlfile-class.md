---
title: Clase CAtlFile | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAtlFile
- ATLFILE/ATL::CAtlFile
- ATLFILE/ATL::CAtlFile::CAtlFile
- ATLFILE/ATL::CAtlFile::Create
- ATLFILE/ATL::CAtlFile::Flush
- ATLFILE/ATL::CAtlFile::GetOverlappedResult
- ATLFILE/ATL::CAtlFile::GetPosition
- ATLFILE/ATL::CAtlFile::GetSize
- ATLFILE/ATL::CAtlFile::LockRange
- ATLFILE/ATL::CAtlFile::Read
- ATLFILE/ATL::CAtlFile::Seek
- ATLFILE/ATL::CAtlFile::SetSize
- ATLFILE/ATL::CAtlFile::UnlockRange
- ATLFILE/ATL::CAtlFile::Write
- ATLFILE/ATL::CAtlFile::m_pTM
dev_langs: C++
helpviewer_keywords: CAtlFile class
ms.assetid: 93ed160b-af2a-448c-9cbe-e5fa46c199bb
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a66e697a3599e7bfeef0f1d5d147e19b668222ce
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="catlfile-class"></a>Clase CAtlFile
Esta clase proporciona un contenedor fino alrededor de las ventanas de API de control de archivos.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class CAtlFile : public CHandle
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAtlFile::CAtlFile](#catlfile)|El constructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAtlFile::Create](#create)|Llame a este método para crear o abrir un archivo.|  
|[CAtlFile::Flush](#flush)|Llamar a este método para borrar los búferes para el archivo y hacer que todos los datos almacenados en búfer se escriban en el archivo.|  
|[CAtlFile::GetOverlappedResult](#getoverlappedresult)|Llamar a este método para obtener los resultados de una operación superpuesta en el archivo.|  
|[CAtlFile::GetPosition](#getposition)|Llame a este método para obtener la posición actual del puntero de archivo del archivo.|  
|[CAtlFile::GetSize](#getsize)|Llame a este método para obtener el tamaño en bytes del archivo.|  
|[CAtlFile::LockRange](#lockrange)|Llame a este método para bloquear una región en el archivo para evitar que otros procesos tengan acceso a él.|  
|[CAtlFile::Read](#read)|Llamar a este método para leer los datos desde un archivo a partir de la posición indicada por el puntero de archivo.|  
|[CAtlFile::Seek](#seek)|Llamar a este método para mover el puntero de archivo del archivo.|  
|[CAtlFile::SetSize](#setsize)|Llamar a este método para establecer el tamaño del archivo.|  
|[CAtlFile::UnlockRange](#unlockrange)|Llamar a este método para desbloquear una región del archivo.|  
|[CAtlFile::Write](#write)|Llame a este método para escribir datos en el archivo a partir de la posición indicada por el puntero de archivo.|  
  
### <a name="protected-data-members"></a>Miembros de datos protegidos  
  
|nombre|Descripción|  
|----------|-----------------|  
|[CAtlFile::m_pTM](#m_ptm)|Puntero a `CAtlTransactionManager` objeto|  
  
## <a name="remarks"></a>Comentarios  
 Utilice esta clase cuando las necesidades de control de archivos son relativamente simples, pero más abstracción que proporciona la API de Windows es necesario, sin incluir las dependencias MFC.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CHandle](../../atl/reference/chandle-class.md)  
  
 `CAtlFile`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlfile.h  
  
##  <a name="catlfile"></a>CAtlFile::CAtlFile  
 El constructor.  
  
```
CAtlFile() throw();
CAtlFile(CAtlTransactionManager* pTM = NULL) throw();
CAtlFile(CAtlFile& file) throw();
explicit CAtlFile(HANDLE hFile) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `file`  
 El objeto de archivo.  
  
 `hFile`  
 El identificador de archivo.  
  
 `pTM`  
 Puntero al objeto CAtlTransactionManager  
  
### <a name="remarks"></a>Comentarios  
 El constructor de copias transfiere la propiedad del identificador del archivo de la versión original `CAtlFile` objeto para el objeto recién creado.  
  
##  <a name="create"></a>CAtlFile::Create  
 Llame a este método para crear o abrir un archivo.  
  
```
HRESULT Create(
    LPCTSTR szFilename,
    DWORD dwDesiredAccess,
    DWORD dwShareMode,
    DWORD dwCreationDisposition,
    DWORD dwFlagsAndAttributes = FILE_ATTRIBUTE_NORMAL,
    LPSECURITY_ATTRIBUTES lpsa = NULL,
    HANDLE hTemplateFile = NULL) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *szFilename*  
 Nombre del archivo.  
  
 `dwDesiredAccess`  
 El acceso deseado. Vea `dwDesiredAccess` en [CreateFile](http://msdn.microsoft.com/library/windows/desktop/aa363858) en el SDK de Windows.  
  
 `dwShareMode`  
 El modo de uso compartido. Vea `dwShareMode` en **CreateFile**.  
  
 `dwCreationDisposition`  
 La disposición de creación. Vea `dwCreationDisposition` en **CreateFile**.  
  
 `dwFlagsAndAttributes`  
 Las marcas y los atributos. Vea `dwFlagsAndAttributes` en **CreateFile**.  
  
 `lpsa`  
 Los atributos de seguridad. Vea *lpSecurityAttributes* en **CreateFile**.  
  
 `hTemplateFile`  
 El archivo de plantilla. Vea `hTemplateFile` en **CreateFile**.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK` resultado correcto o error `HRESULT` en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Llamadas [CreateFile](http://msdn.microsoft.com/library/windows/desktop/aa363858) para crear o abrir el archivo.  
  
##  <a name="flush"></a>CAtlFile::Flush  
 Llamar a este método para borrar los búferes para el archivo y hacer que todos los datos almacenados en búfer se escriban en el archivo.  
  
```
HRESULT Flush() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK` resultado correcto o error `HRESULT` en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Llamadas [FlushFileBuffers](http://msdn.microsoft.com/library/windows/desktop/aa364439) para vaciar los datos almacenados en búfer en el archivo.  
  
##  <a name="getoverlappedresult"></a>CAtlFile::GetOverlappedResult  
 Llamar a este método para obtener los resultados de una operación superpuesta en el archivo.  
  
```
HRESULT GetOverlappedResult(
    LPOVERLAPPED pOverlapped,
    DWORD& dwBytesTransferred,
    BOOL bWait) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `pOverlapped`  
 La estructura superpuesta. Vea `lpOverlapped` en [GetOverlappedResult](http://msdn.microsoft.com/library/windows/desktop/ms683209) en el SDK de Windows.  
  
 *dwBytesTransferred*  
 Los bytes se transfieren. Vea *lpNumberOfBytesTransferred* en `GetOverlappedResult`.  
  
 `bWait`  
 La opción de espera. Vea `bWait` en `GetOverlappedResult`.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK` resultado correcto o error `HRESULT` en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Llamadas [GetOverlappedResult](http://msdn.microsoft.com/library/windows/desktop/ms683209) para obtener los resultados de una operación superpuesta en el archivo.  
  
##  <a name="getposition"></a>CAtlFile::GetPosition  
 Llamar a este método para obtener la posición actual del puntero de archivo.  
  
```
HRESULT GetPosition(ULONGLONG& nPos) const throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `nPos`  
 La posición en bytes.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK` resultado correcto o error `HRESULT` en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Llamadas [SetFilePointer](http://msdn.microsoft.com/library/windows/desktop/aa365541) para obtener la posición actual del puntero de archivo.  
  
##  <a name="getsize"></a>CAtlFile::GetSize  
 Llame a este método para obtener el tamaño en bytes del archivo.  
  
```
HRESULT GetSize(ULONGLONG& nLen) const throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `nLen`  
 El número de bytes en el archivo.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK` resultado correcto o error `HRESULT` en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Llamadas [GetFileSize](http://msdn.microsoft.com/library/windows/desktop/aa364955) para obtener el tamaño en bytes del archivo.  
  
##  <a name="lockrange"></a>CAtlFile::LockRange  
 Llame a este método para bloquear una región en el archivo para evitar que otros procesos tengan acceso a él.  
  
```
HRESULT LockRange(ULONGLONG nPos, ULONGLONG nCount) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `nPos`  
 La posición en el archivo donde debe comenzar el bloqueo.  
  
 `nCount`  
 La longitud del intervalo de bytes que se bloquee.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK` resultado correcto o error `HRESULT` en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Llamadas [encontraba](http://msdn.microsoft.com/library/windows/desktop/aa365202) para bloquear una región en el archivo. El bloqueo de bytes en un archivo impide que otros procesos obtengan acceso a dichos bytes. Se puede bloquear más de una región de un archivo, pero no las áreas superpuestas se permiten. Cuando haya desbloqueado una región, con [CAtlFile::UnlockRange](#unlockrange), el intervalo de bytes debe corresponder exactamente con la región que se ha bloqueado anteriormente. `LockRange`no combina regiones adyacentes; Si dos regiones bloqueadas son adyacentes, debe desbloquear a cada uno de ellos por separado.  
  
##  <a name="m_ptm"></a>CAtlFile::m_pTM  
 Puntero a un `CAtlTransactionManager` objeto.  
  
```
CAtlTransactionManager* m_pTM;
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="read"></a>CAtlFile::Read  
 Llamar a este método para leer los datos desde un archivo a partir de la posición indicada por el puntero de archivo.  
  
```
HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize) throw();

HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize,
    DWORD& nBytesRead) throw();

HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize,
    LPOVERLAPPED pOverlapped) throw();

HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize,
    LPOVERLAPPED pOverlapped,
    LPOVERLAPPED_COMPLETION_ROUTINE pfnCompletionRoutine) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `pBuffer`  
 Puntero al búfer que recibirá los datos leídos desde el archivo.  
  
 `nBufSize`  
 El tamaño del búfer en bytes.  
  
 `nBytesRead`  
 Número de bytes leídos.  
  
 `pOverlapped`  
 La estructura superpuesta. Vea `lpOverlapped` en [ReadFile](http://msdn.microsoft.com/library/windows/desktop/aa365467) en el SDK de Windows.  
  
 `pfnCompletionRoutine`  
 La rutina de finalización. Vea *lpCompletionRoutine* en [ReadFileEx](http://msdn.microsoft.com/library/windows/desktop/aa365468) en el SDK de Windows.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK` resultado correcto o error `HRESULT` en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Llamar las tres primeras formas [ReadFile](http://msdn.microsoft.com/library/windows/desktop/aa365467), la última [ReadFileEx](http://msdn.microsoft.com/library/windows/desktop/aa365468) para leer datos desde el archivo. Use [CAtlFile::Seek](#seek) para mover el puntero de archivo.  
  
##  <a name="seek"></a>CAtlFile::Seek  
 Llamar a este método para mover el puntero de archivo del archivo.  
  
```
HRESULT Seek(
    LONGLONG nOffset,
    DWORD dwFrom = FILE_CURRENT) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `nOffset`  
 El desplazamiento desde el punto inicial proporcionado por `dwFrom`.  
  
 `dwFrom`  
 El punto de partida (FILE_BEGIN, FILE_CURRENT o FILE_END).  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK` resultado correcto o error `HRESULT` en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Llamadas [SetFilePointer](http://msdn.microsoft.com/library/windows/desktop/aa365541) para mover el puntero de archivo.  
  
##  <a name="setsize"></a>CAtlFile::SetSize  
 Llamar a este método para establecer el tamaño del archivo.  
  
```
HRESULT SetSize(ULONGLONG nNewLen) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `nNewLen`  
 La nueva longitud del archivo en bytes.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK` resultado correcto o error `HRESULT` en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Llamadas [SetFilePointer](http://msdn.microsoft.com/library/windows/desktop/aa365541) y [SetEndOfFile](http://msdn.microsoft.com/library/windows/desktop/aa365531) para establecer el tamaño del archivo. Una vez devuelta, se coloca el puntero de archivo al final del archivo.  
  
##  <a name="unlockrange"></a>CAtlFile::UnlockRange  
 Llamar a este método para desbloquear una región del archivo.  
  
```
HRESULT UnlockRange(ULONGLONG nPos, ULONGLONG nCount) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `nPos`  
 La posición en el archivo donde debe comenzar el desbloqueo.  
  
 `nCount`  
 La longitud del rango de bytes que se pueden desbloquear.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK` resultado correcto o error `HRESULT` en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Llamadas [UnlockFile](http://msdn.microsoft.com/library/windows/desktop/aa365715) para desbloquear una región del archivo.  
  
##  <a name="write"></a>CAtlFile::Write  
 Llame a este método para escribir datos en el archivo a partir de la posición indicada por el puntero de archivo.  
  
```
HRESULT Write(
    LPCVOID pBuffer,
    DWORD nBufSize,
    LPOVERLAPPED pOverlapped,
    LPOVERLAPPED_COMPLETION_ROUTINE pfnCompletionRoutine) throw();

HRESULT Write(
    LPCVOID pBuffer,
    DWORD nBufSize,
    DWORD* pnBytesWritten = NULL) throw();

HRESULT Write(
    LPCVOID pBuffer,
    DWORD nBufSize,
    LPOVERLAPPED pOverlapped) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `pBuffer`  
 El búfer que contiene los datos se escriban en el archivo.  
  
 `nBufSize`  
 El número de bytes que se transfieren desde el búfer.  
  
 `pOverlapped`  
 La estructura superpuesta. Vea `lpOverlapped` en [WriteFile](http://msdn.microsoft.com/library/windows/desktop/aa365747) en el SDK de Windows.  
  
 `pfnCompletionRoutine`  
 La rutina de finalización. Vea *lpCompletionRoutine* en [WriteFileEx](http://msdn.microsoft.com/library/windows/desktop/aa365748) en el SDK de Windows.  
  
 `pnBytesWritten`  
 Bytes escritos.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK` resultado correcto o error `HRESULT` en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Llamar las tres primeras formas [WriteFile](http://msdn.microsoft.com/library/windows/desktop/aa365747), las llamadas última [WriteFileEx](http://msdn.microsoft.com/library/windows/desktop/aa365748) para escribir datos en el archivo. Use [CAtlFile::Seek](#seek) para mover el puntero de archivo.  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo de marquesina](../../visual-cpp-samples.md)   
 [Información general de clases](../../atl/atl-class-overview.md)   
 [CHandle (clase)](../../atl/reference/chandle-class.md)
