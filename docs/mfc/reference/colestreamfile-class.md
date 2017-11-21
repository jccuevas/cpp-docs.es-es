---
title: Clase COleStreamFile | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleStreamFile
- AFXOLE/COleStreamFile
- AFXOLE/COleStreamFile::COleStreamFile
- AFXOLE/COleStreamFile::Attach
- AFXOLE/COleStreamFile::CreateMemoryStream
- AFXOLE/COleStreamFile::CreateStream
- AFXOLE/COleStreamFile::Detach
- AFXOLE/COleStreamFile::GetStream
- AFXOLE/COleStreamFile::OpenStream
dev_langs: C++
helpviewer_keywords:
- COleStreamFile [MFC], COleStreamFile
- COleStreamFile [MFC], Attach
- COleStreamFile [MFC], CreateMemoryStream
- COleStreamFile [MFC], CreateStream
- COleStreamFile [MFC], Detach
- COleStreamFile [MFC], GetStream
- COleStreamFile [MFC], OpenStream
ms.assetid: e4f93698-e17c-4a18-a7c0-4b4df8eb4d93
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1c7b9e26013a505f5de137797964ed19376569a2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
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
|[COleStreamFile::Attach](#attach)|Asocia un flujo con el objeto.|  
|[COleStreamFile::CreateMemoryStream](#creatememorystream)|Crea una secuencia de la memoria global y lo asocia con el objeto.|  
|[COleStreamFile::CreateStream](#createstream)|Crea una secuencia y lo asocia con el objeto.|  
|[COleStreamFile::Detach](#detach)|Desasocia el flujo del objeto.|  
|[COleStreamFile::GetStream](#getstream)|Devuelve la secuencia actual.|  
|[COleStreamFile::OpenStream](#openstream)|Abre un flujo de datos y lo asocia con el objeto de forma segura.|  
  
## <a name="remarks"></a>Comentarios  
 Un `IStorage` el objeto debe existir antes de que la secuencia se puede abrir o crear a menos que sea una secuencia de memoria.  
  
 `COleStreamFile`exactamente igual que se manipulan los objetos [CFile](../../mfc/reference/cfile-class.md) objetos.  
  
 Para obtener más información sobre cómo manipular los flujos y almacenamiento, vea el artículo [contenedores: archivos compuestos](../../mfc/containers-compound-files.md)...  
  
 Para obtener más información, consulte [IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034) y [IStorage](http://msdn.microsoft.com/library/windows/desktop/aa380015) del SDK de Windows.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 `COleStreamFile`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxole.h  
  
##  <a name="attach"></a>COleStreamFile::Attach  
 Asocia la secuencia OLE suministrada con el `COleStreamFile` objeto.  
  
```  
void Attach(LPSTREAM lpStream);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpStream`  
 Apunta a la secuencia OLE ( `IStream`) que se asociará con el objeto. No puede ser **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 El objeto no ya debe estar asociado a un flujo OLE.  
  
 Para obtener más información, consulte [IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034) del SDK de Windows.  
  
##  <a name="colestreamfile"></a>COleStreamFile::COleStreamFile  
 Crea un objeto `COleStreamFile`.  
  
```  
COleStreamFile(LPSTREAM lpStream = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpStream`  
 Puntero a la secuencia OLE que se asociará con el objeto.  
  
### <a name="remarks"></a>Comentarios  
 Si `lpStream` es **NULL**, el objeto no está asociado a un flujo OLE, de lo contrario, el objeto está asociado a la secuencia proporcionada de OLE.  
  
 Para obtener más información, consulte [IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034) del SDK de Windows.  
  
##  <a name="creatememorystream"></a>COleStreamFile::CreateMemoryStream  
 Con seguridad crea una nueva secuencia de memoria compartida global donde un error es una condición normal, se esperaba.  
  
```  
BOOL CreateMemoryStream(CFileException* pError = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `pError`  
 Apunta a un [CFileException](../../mfc/reference/cfileexception-class.md) objeto o **NULL** que indica el estado de finalización de la operación de creación. Proporcione este parámetro si desea supervisar las posibles excepciones que se genera al intentar crear la secuencia.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la secuencia se crea correctamente; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 La memoria está asignada por el subsistema OLE.  
  
 Para obtener más información, consulte [CreateStreamOnHGlobal](http://msdn.microsoft.com/library/windows/desktop/aa378980) del SDK de Windows.  
  
##  <a name="createstream"></a>COleStreamFile::CreateStream  
 Con seguridad crea una nueva secuencia en el objeto de almacenamiento proporcionado donde un error es una condición normal, se esperaba.  
  
```  
BOOL CreateStream(
    LPSTORAGE lpStorage,  
    LPCTSTR lpszStreamName,  
    DWORD nOpenFlags = modeReadWrite|shareExclusive|modeCreate,  
    CFileException* pError = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpStorage`  
 Señala al objeto de almacenamiento OLE que contiene la secuencia que se va a crear. No puede ser **NULL**.  
  
 `lpszStreamName`  
 Nombre de la secuencia que se va a crear. No puede ser **NULL**.  
  
 `nOpenFlags`  
 Modo de acceso que se utilizará al abrir la secuencia. Exclusivo, lectura y escritura y crear modos se usan de forma predeterminada. Para obtener una lista completa de los modos disponibles, vea [CFile::CFile](../../mfc/reference/cfile-class.md#cfile).  
  
 `pError`  
 Apunta a un [CFileException](../../mfc/reference/cfileexception-class.md) objeto o **NULL**. Proporcione este parámetro si desea supervisar las posibles excepciones que se genera al intentar crear la secuencia.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la secuencia se crea correctamente; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Si se produce un error en la apertura, se producirá una excepción de archivo y `pError` no **NULL**.  
  
 Para obtener más información, consulte [IStorage::CreateStream](http://msdn.microsoft.com/library/windows/desktop/aa380020) en el SDK de Windows.  
  
##  <a name="detach"></a>COleStreamFile::Detach  
 Desasocia el flujo del objeto sin cerrar la secuencia.  
  
```  
LPSTREAM Detach();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la secuencia ( `IStream`) que estaba asociado con el objeto.  
  
### <a name="remarks"></a>Comentarios  
 Debe cerrar la secuencia de algún otro modo antes de que finalice el programa.  
  
 Para obtener más información, consulte [IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034) del SDK de Windows.  
  
##  <a name="getstream"></a>COleStreamFile::GetStream  
 Llame a esta función para devolver un puntero a la secuencia actual.  
  
```  
IStream* GetStream() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la interfaz de secuencia actual ( [IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034)).  
  
##  <a name="openstream"></a>COleStreamFile::OpenStream  
 Abre un flujo existente.  
  
```  
BOOL OpenStream(
    LPSTORAGE lpStorage,  
    LPCTSTR lpszStreamName,  
    DWORD nOpenFlags = modeReadWrite|shareExclusive,  
    CFileException* pError = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpStorage`  
 Señala al objeto de almacenamiento OLE que contiene la secuencia que se va a abrir. No puede ser **NULL**.  
  
 `lpszStreamName`  
 Nombre de la secuencia que se puede abrir. No puede ser **NULL**.  
  
 `nOpenFlags`  
 Modo de acceso que se utilizará al abrir la secuencia. Exclusivo y lectura/escritura se usan los modos de forma predeterminada. Para obtener la lista completa de los modos disponibles, consulte [CFile::CFile](../../mfc/reference/cfile-class.md#cfile).  
  
 `pError`  
 Apunta a un [CFileException](../../mfc/reference/cfileexception-class.md) objeto o **NULL**. Proporcione este parámetro si desea supervisar las posibles excepciones que se genera al intentar abrir la secuencia.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el flujo se abre correctamente; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Si se produce un error en la apertura, se producirá una excepción de archivo y `pError` no **NULL**.  
  
 Para obtener más información, consulte [IStorage::OpenStream](http://msdn.microsoft.com/library/windows/desktop/aa380025) en el SDK de Windows.  
  
## <a name="see-also"></a>Vea también  
 [CFile (clase)](../../mfc/reference/cfile-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)



