---
title: Clase COleStreamFile | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleStreamFile
dev_langs:
- C++
helpviewer_keywords:
- data streams [C++]
- streams [C++], OLE
- data streams [C++], OLE
- structured storage in OLE
- OLE structured storage [C++]
- OLE [C++], streams of data
- COleStreamFile class
ms.assetid: e4f93698-e17c-4a18-a7c0-4b4df8eb4d93
caps.latest.revision: 22
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
ms.openlocfilehash: 0840d365f4179da0ad680256688eaf9484cb3cd8
ms.lasthandoff: 02/24/2017

---
# <a name="colestreamfile-class"></a>Clase COleStreamFile
Representa un flujo de datos ( `IStream`) en un archivo compuesto como parte de almacenamiento estructurado OLE.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class COleStreamFile : public CFile  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[COleStreamFile::COleStreamFile](#colestreamfile)|Construye un objeto `COleStreamFile`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[COleStreamFile::Attach](#attach)|Asocia una secuencia con el objeto.|  
|[COleStreamFile::CreateMemoryStream](#creatememorystream)|Crea una secuencia de la memoria global y lo asocia con el objeto.|  
|[COleStreamFile::CreateStream](#createstream)|Crea una secuencia y lo asocia con el objeto.|  
|[COleStreamFile::Detach](#detach)|Desasocia la secuencia del objeto.|  
|[COleStreamFile::GetStream](#getstream)|Devuelve la secuencia actual.|  
|[COleStreamFile::OpenStream](#openstream)|Abre una secuencia y lo asocia con el objeto de forma segura.|  
  
## <a name="remarks"></a>Comentarios  
 Una `IStorage` debe existir antes de que la secuencia se puede abrir o crear a menos que sea una secuencia de memoria.  
  
 `COleStreamFile`exactamente como se manipulan los objetos [CFile](../../mfc/reference/cfile-class.md) objetos.  
  
 Para obtener más información sobre cómo manipular los flujos y almacenamiento, consulte el artículo [contenedores: archivos compuestos](../../mfc/containers-compound-files.md)...  
  
 Para obtener más información, consulte [IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034) y [IStorage](http://msdn.microsoft.com/library/windows/desktop/aa380015) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 `COleStreamFile`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxole.h  
  
##  <a name="a-nameattacha--colestreamfileattach"></a><a name="attach"></a>COleStreamFile::Attach  
 Asocia el flujo OLE proporcionado con el `COleStreamFile` objeto.  
  
```  
void Attach(LPSTREAM lpStream);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpStream`  
 Apunta a la secuencia OLE ( `IStream`) que se asociará con el objeto. No puede ser **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 El objeto no ya debe estar asociado con una secuencia OLE.  
  
 Para obtener más información, consulte [IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namecolestreamfilea--colestreamfilecolestreamfile"></a><a name="colestreamfile"></a>COleStreamFile::COleStreamFile  
 Crea un objeto `COleStreamFile`.  
  
```  
COleStreamFile(LPSTREAM lpStream = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpStream`  
 Puntero a la secuencia OLE que se asociará con el objeto.  
  
### <a name="remarks"></a>Comentarios  
 Si `lpStream` es **NULL**, el objeto no está asociado con una secuencia OLE, de lo contrario, el objeto está asociado a la secuencia proporcionada de OLE.  
  
 Para obtener más información, consulte [IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namecreatememorystreama--colestreamfilecreatememorystream"></a><a name="creatememorystream"></a>COleStreamFile::CreateMemoryStream  
 Con seguridad crea una nueva secuencia de memoria compartida global donde un error es una situación normal y esperada.  
  
```  
BOOL CreateMemoryStream(CFileException* pError = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `pError`  
 Apunta a un [CFileException](../../mfc/reference/cfileexception-class.md) objeto o **NULL** que indica el estado de finalización de la operación de creación. Proporcione este parámetro si desea supervisar las posibles excepciones generadas al intentar crear la secuencia.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la secuencia se ha creado correctamente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 La memoria está asignada por el subsistema OLE.  
  
 Para obtener más información, consulte [CreateStreamOnHGlobal](http://msdn.microsoft.com/library/windows/desktop/aa378980) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namecreatestreama--colestreamfilecreatestream"></a><a name="createstream"></a>COleStreamFile::CreateStream  
 Con seguridad, crea una nueva secuencia en el objeto de almacenamiento proporcionado donde un error es una situación normal y esperada.  
  
```  
BOOL CreateStream(
    LPSTORAGE lpStorage,  
    LPCTSTR lpszStreamName,  
    DWORD nOpenFlags = modeReadWrite|shareExclusive|modeCreate,  
    CFileException* pError = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpStorage`  
 Señala al objeto OLE de almacenamiento que contiene la secuencia que se va a crear. No puede ser **NULL**.  
  
 `lpszStreamName`  
 Nombre de la secuencia que se va a crear. No puede ser **NULL**.  
  
 `nOpenFlags`  
 Modo de acceso que se utilizará al abrir la secuencia. Exclusivo, lectura y escritura y crear modos se utilizan de forma predeterminada. Para obtener una lista completa de los modos disponibles, consulte [CFile::CFile](../../mfc/reference/cfile-class.md#cfile).  
  
 `pError`  
 Apunta a un [CFileException](../../mfc/reference/cfileexception-class.md) objeto o **NULL**. Proporcione este parámetro si desea supervisar las posibles excepciones generadas al intentar crear la secuencia.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la secuencia se ha creado correctamente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Si se produce un error en la apertura, se producirá una excepción de archivo y `pError` no **NULL**.  
  
 Para obtener más información, consulte [IStorage::CreateStream](http://msdn.microsoft.com/library/windows/desktop/aa380020) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namedetacha--colestreamfiledetach"></a><a name="detach"></a>COleStreamFile::Detach  
 Desasocia la secuencia del objeto sin cerrar la secuencia.  
  
```  
LPSTREAM Detach();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la secuencia ( `IStream`) que estaba asociado con el objeto.  
  
### <a name="remarks"></a>Comentarios  
 La secuencia debe cerrarse de algún otro modo antes de que finalice el programa.  
  
 Para obtener más información, consulte [IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namegetstreama--colestreamfilegetstream"></a><a name="getstream"></a>COleStreamFile::GetStream  
 Llame a esta función para devolver un puntero a la secuencia actual.  
  
```  
IStream* GetStream() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la interfaz de la secuencia actual ( [IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034)).  
  
##  <a name="a-nameopenstreama--colestreamfileopenstream"></a><a name="openstream"></a>COleStreamFile::OpenStream  
 Abre una secuencia existente.  
  
```  
BOOL OpenStream(
    LPSTORAGE lpStorage,  
    LPCTSTR lpszStreamName,  
    DWORD nOpenFlags = modeReadWrite|shareExclusive,  
    CFileException* pError = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpStorage`  
 Señala al objeto OLE de almacenamiento que contiene la secuencia que se va a abrir. No puede ser **NULL**.  
  
 `lpszStreamName`  
 Nombre de la secuencia que se va a abrir. No puede ser **NULL**.  
  
 `nOpenFlags`  
 Modo de acceso que se utilizará al abrir la secuencia. Exclusivo y predeterminada se usan los modos de lectura y escritura. Para obtener una lista completa de los modos disponibles, consulte [CFile::CFile](../../mfc/reference/cfile-class.md#cfile).  
  
 `pError`  
 Apunta a un [CFileException](../../mfc/reference/cfileexception-class.md) objeto o **NULL**. Proporcione este parámetro si desea supervisar las posibles excepciones que se genera al intentar abrir la secuencia.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el flujo se abre correctamente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Si se produce un error en la apertura, se producirá una excepción de archivo y `pError` no **NULL**.  
  
 Para obtener más información, consulte [IStorage::OpenStream](http://msdn.microsoft.com/library/windows/desktop/aa380025) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
## <a name="see-also"></a>Vea también  
 [CFile (clase)](../../mfc/reference/cfile-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)




