---
title: CInternetFile (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CInternetFile
- AFXINET/CInternetFile
- AFXINET/CInternetFile::CInternetFile
- AFXINET/CInternetFile::Abort
- AFXINET/CInternetFile::Close
- AFXINET/CInternetFile::Flush
- AFXINET/CInternetFile::GetLength
- AFXINET/CInternetFile::Read
- AFXINET/CInternetFile::ReadString
- AFXINET/CInternetFile::Seek
- AFXINET/CInternetFile::SetReadBufferSize
- AFXINET/CInternetFile::SetWriteBufferSize
- AFXINET/CInternetFile::Write
- AFXINET/CInternetFile::WriteString
- AFXINET/CInternetFile::m_hFile
dev_langs:
- C++
helpviewer_keywords:
- CInternetFile [MFC], CInternetFile
- CInternetFile [MFC], Abort
- CInternetFile [MFC], Close
- CInternetFile [MFC], Flush
- CInternetFile [MFC], GetLength
- CInternetFile [MFC], Read
- CInternetFile [MFC], ReadString
- CInternetFile [MFC], Seek
- CInternetFile [MFC], SetReadBufferSize
- CInternetFile [MFC], SetWriteBufferSize
- CInternetFile [MFC], Write
- CInternetFile [MFC], WriteString
- CInternetFile [MFC], m_hFile
ms.assetid: 96935681-ee71-4a8d-9783-5abc7b3e6f10
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ed85edeaf5400805d4628e10acab4cdf4af52082
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43202735"
---
# <a name="cinternetfile-class"></a>CInternetFile (clase)
Permite el acceso a archivos en sistemas remotos que utilizan protocolos de Internet.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CInternetFile : public CStdioFile  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="protected-constructors"></a>Constructores protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CInternetFile::CInternetFile](#cinternetfile)|Construye un objeto `CInternetFile`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CInternetFile::Abort](#abort)|Cierra el archivo, se omitirá todas las advertencias y errores.|  
|[CInternetFile::Close](#close)|Cierra un `CInternetFile` y libera sus recursos.|  
|[CInternetFile::Flush](#flush)|Vuelca el contenido del búfer de escritura y se asegura de que los datos en memoria se escriben en el equipo de destino.|  
|[CInternetFile::GetLength](#getlength)|Devuelve el tamaño del archivo.|  
|[CInternetFile:: Read](#read)|Lee el número de bytes especificados.|  
|[CInternetFile::ReadString](#readstring)|Lee una secuencia de caracteres.|  
|[CInternetFile::Seek](#seek)|Recoloca el puntero en un archivo abierto.|  
|[CInternetFile::SetReadBufferSize](#setreadbuffersize)|Establece el tamaño del búfer donde se leerán los datos.|  
|[CInternetFile::SetWriteBufferSize](#setwritebuffersize)|Establece el tamaño del búfer donde se escribirán los datos.|  
|[CInternetFile:: Write](#write)|Escribe el número de bytes especificados.|  
|[CInternetFile::WriteString](#writestring)|Escribe una cadena terminada en null en un archivo.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CInternetFile::operator HINTERNET](#operator_hinternet)|Un operador de conversión para un identificador de Internet.|  
  
### <a name="protected-data-members"></a>Miembros de datos protegidos  
  
|nombre|Descripción|  
|----------|-----------------|  
|[CInternetFile::m_hFile](#m_hfile)|Un identificador a un archivo.|  
  
## <a name="remarks"></a>Comentarios  
 Proporciona una clase base para el [CHttpFile](../../mfc/reference/chttpfile-class.md) y [CGopherFile](../../mfc/reference/cgopherfile-class.md) clases de archivos. No crear nunca un `CInternetFile` objeto directamente. En su lugar, cree un objeto de uno de sus clases derivadas mediante una llamada a [CGopherConnection:: OpenFile](../../mfc/reference/cgopherconnection-class.md#openfile) o [CHttpConnection:: OpenRequest](../../mfc/reference/chttpconnection-class.md#openrequest). También puede crear un `CInternetFile` objeto mediante una llamada a [CFtpConnection:: OpenFile](../../mfc/reference/cftpconnection-class.md#openfile).  
  
 El `CInternetFile` funciones miembro `Open`, `LockRange`, `UnlockRange`, y `Duplicate` no se implementan para `CInternetFile`. Si se llama a estas funciones en un `CInternetFile` objeto, obtendrá un [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).  
  
 Para obtener más información sobre cómo `CInternetFile` funciona con las clases de Internet de MFC, vea el artículo [Internet programar con WinInet](../../mfc/win32-internet-extensions-wininet.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 [CStdioFile](../../mfc/reference/cstdiofile-class.md)  
  
 `CInternetFile`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxinet.h  
  
##  <a name="abort"></a>  CInternetFile::Abort  
 Cierra el archivo asociado a este objeto y hace que el archivo no esté disponible para lectura o escritura.  
  
```  
virtual void Abort();
```  
  
### <a name="remarks"></a>Comentarios  
 Si no ha cerrado el archivo antes de destruir el objeto, el destructor cierra automáticamente.  
  
 Cuando el control de excepciones, `Abort` difiere [cerrar](#close) en dos aspectos importantes. En primer lugar, el `Abort` función no produce una excepción en errores porque omite los errores. Segundo, `Abort` no **ASSERT** si el archivo no se abrió o cerró anteriormente.  
  
##  <a name="cinternetfile"></a>  CInternetFile::CInternetFile  
 Esta función miembro se llama cuando un `CInternetFile` se crea el objeto.  
  
```  
CInternetFile(
    HINTERNET hFile,  
    LPCTSTR pstrFileName,  
    CInternetConnection* pConnection,  
    BOOL bReadMode);

 
CInternetFile(
    HINTERNET hFile,  
    HINTERNET hSession,  
    LPCTSTR pstrFileName,  
    LPCTSTR pstrServer,  
    DWORD_PTR dwContext,  
    BOOL bReadMode);
```  
  
### <a name="parameters"></a>Parámetros  
 *hFile*  
 Identificador de un archivo de Internet.  
  
 *pstrFileName*  
 Un puntero a una cadena que contiene el nombre de archivo.  
  
 *pConnection*  
 Un puntero a un [CInternetConnection](../../mfc/reference/cinternetconnection-class.md) objeto.  
  
 *bReadMode*  
 Indica si el archivo es de solo lectura.  
  
 *hSession*  
 Identificador de sesión de Internet.  
  
 *pstrServer*  
 Un puntero a una cadena que contiene el nombre del servidor.  
  
 *dwContext*  
 El identificador de contexto para el `CInternetFile` objeto. Consulte [Fundamentos de WinInet](../../mfc/wininet-basics.md) para obtener más información sobre el identificador de contexto.  
  
### <a name="remarks"></a>Comentarios  
 No crear nunca un `CInternetFile` objeto directamente. En su lugar, cree un objeto de uno de sus clases derivadas mediante una llamada a [CGopherConnection:: OpenFile](../../mfc/reference/cgopherconnection-class.md#openfile) o [CHttpConnection:: OpenRequest](../../mfc/reference/chttpconnection-class.md#openrequest). También puede crear un `CInternetFile` objeto mediante una llamada a [CFtpConnection:: OpenFile](../../mfc/reference/cftpconnection-class.md#openfile).  
  
##  <a name="close"></a>  CInternetFile::Close  
 Cierra un `CInternetFile` y libera sus recursos.  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>Comentarios  
 Si se abrió el archivo para escribir en él, hay una llamada implícita a [vaciar](#flush) garantizar que todos los datos almacenados en búfer se escriban en el host. Debe llamar a `Close` cuando haya terminado de usar un archivo.  
  
##  <a name="flush"></a>  CInternetFile::Flush  
 Llame a esta función miembro para vaciar el contenido del búfer de escritura.  
  
```  
virtual void Flush();
```  
  
### <a name="remarks"></a>Comentarios  
 Use `Flush` para garantizar que todos los datos en memoria se ha escrito realmente en el equipo de destino y para asegurarse de que se ha completado la transacción con el equipo host. `Flush` solo es efectivo en `CInternetFile` objetos abrir para escritura.  
  
##  <a name="getlength"></a>  CInternetFile::GetLength  
 Devuelve el tamaño del archivo.  
  
```  
virtual ULONGLONG GetLength() const;  
```  
  
##  <a name="m_hfile"></a>  CInternetFile::m_hFile  
 Un identificador para el archivo asociado a este objeto.  
  
```  
HINTERNET m_hFile;  
```  
  
##  <a name="operator_hinternet"></a>  CInternetFile::operator HINTERNET  
 Utilice este operador para obtener el identificador de Windows para la sesión actual de Internet.  
  
```  
operator HINTERNET() const;  
```  
  
##  <a name="read"></a>  CInternetFile:: Read  
 Llame a esta función miembro para leer en la memoria determinada, comenzando en *lpvBuf*, el número especificado de bytes, *nCount*.  
  
```  
virtual UINT Read(
    void* lpBuf,  
    UINT nCount);
```  
  
### <a name="parameters"></a>Parámetros  
 *lpBuf*  
 Puntero a una dirección de memoria para la que se leen datos de archivo.  
  
 *nCount*  
 Número de bytes que se escribirán.  
  
### <a name="return-value"></a>Valor devuelto  
 Número de bytes que se transfieren al búfer. El valor devuelto puede ser menor que *nCount* si se alcanzó el final del archivo.  
  
### <a name="remarks"></a>Comentarios  
 La función devuelve el número de bytes leídos realmente, un número que puede ser menor que *nCount* si finaliza el archivo. Si se produce un error al leer el archivo, la función produce un [CInternetException](../../mfc/reference/cinternetexception-class.md) objeto que describe el error. Tenga en cuenta que leer más allá del final del archivo no se considera un error y no se generará ninguna excepción.  
  
 Para asegurarse de que se recuperan todos los datos, una aplicación debe seguir llamar a la `CInternetFile::Read` método hasta que el método devuelve cero.  
  
##  <a name="readstring"></a>  CInternetFile::ReadString  
 Llame a esta función miembro para leer una secuencia de caracteres hasta que encuentra un carácter de nueva línea.  
  
```  
virtual BOOL ReadString(CString& rString);

 
virtual LPTSTR ReadString(
    LPTSTR pstr,  
    UINT nMax);
```  
  
### <a name="parameters"></a>Parámetros  
 *pStr*  
 Un puntero a una cadena que recibirá la línea que se va a leer.  
  
 *Nmáx.*  
 El número máximo de caracteres que leer.  
  
 *rString*  
 Una referencia a la [CString](../../atl-mfc-shared/reference/cstringt-class.md) objeto que recibe la línea de lectura.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al búfer que contiene los datos sin formato que se recuperan de la [CInternetFile](../../mfc/reference/cinternetfile-class.md) objeto. Independientemente del tipo de datos del búfer pasado a este método, no realiza las manipulaciones de los datos (por ejemplo, la conversión a Unicode), por lo que debe asignar los datos devueltos a la estructura se espera que, como si el **void** <strong>\*</strong> devolvió el tipo.  
  
 NULL si se alcanzó el final de archivo sin necesidad de leer los datos; o bien, si se alcanzó boolean, FALSE si el final de archivo sin necesidad de leer los datos.  
  
### <a name="remarks"></a>Comentarios  
 La función coloca la línea resultante en la memoria al que hace referencia el *pstr* parámetro. Deja de leer caracteres cuando alcanza el número máximo de caracteres, especificado por *Nmáx*. El búfer siempre recibe un carácter nulo de terminación.  
  
 Si se llama a `ReadString` sin llamar primero a [SetReadBufferSize](#setreadbuffersize), obtendrá un búfer de 4096 bytes.  
  
##  <a name="seek"></a>  CInternetFile::Seek  
 Llame a esta función miembro para colocar el puntero en un archivo abierto anteriormente.  
  
```  
virtual ULONGLONG Seek(
    LONGLONG lOffset,  
    UINT nFrom);
```  
  
### <a name="parameters"></a>Parámetros  
 *lOffset*  
 Desplazamiento en bytes para mover el puntero de lectura/escritura en el archivo.  
  
 *nde*  
 Referencia relativa para el desplazamiento. Debe ser uno de los siguientes valores:  
  
- `CFile::begin` Mueva el puntero de archivo *lOff* reenvían bytes desde el principio del archivo.  
  
- `CFile::current` Mueva el puntero de archivo *lOff* bytes desde la posición actual en el archivo.  
  
- `CFile::end` Mueva el puntero de archivo *lOff* bytes desde el final del archivo. *lOff* debe ser negativo para buscar en las existentes archivo; positivo buscarán valores más allá del final del archivo.  
  
### <a name="return-value"></a>Valor devuelto  
 El desplazamiento desde el principio del archivo si la posición solicitada es legal; nuevo en bytes en caso contrario, el valor es indefinido y un [CInternetException](../../mfc/reference/cinternetexception-class.md) se produce el objeto.  
  
### <a name="remarks"></a>Comentarios  
 El `Seek` función permite el acceso aleatorio al contenido de un archivo, mueva el puntero una cantidad especificada, absoluta o relativa. No hay datos que se lean durante la búsqueda.  
  
 En este momento, solo se admite una llamada a esta función miembro de datos asociados con `CHttpFile` objetos. No se admite para las solicitudes FTP o gopher. Si se llama a `Seek` uno de estos servicios no compatibles, le pasa volver al código de error de Win32 ERROR_INTERNET_INVALID_OPERATION.  
  
 Cuando se abre un archivo, es el puntero de archivo en el desplazamiento 0, el principio del archivo.  
  
> [!NOTE]
>  Uso de `Seek` puede provocar una llamada implícita a [vaciar](#flush).  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de la implementación de la clase base ( [CFile::Seek](../../mfc/reference/cfile-class.md#seek)).  
  
##  <a name="setreadbuffersize"></a>  CInternetFile::SetReadBufferSize  
 Llame a esta función miembro para establecer el tamaño del búfer de lectura temporal usado por un `CInternetFile`-objeto derivado.  
  
```  
BOOL SetReadBufferSize(UINT nReadSize);
```  
  
### <a name="parameters"></a>Parámetros  
 *nReadSize*  
 Tamaño deseado del búfer en bytes.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, la función de Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) puede llamarse para determinar la causa del error.  
  
### <a name="remarks"></a>Comentarios  
 Las APIs WinInet subyacente no realizar almacenamiento en búfer, así que elija un tamaño de búfer que permite que la aplicación leer datos de forma eficaz, independientemente de la cantidad de datos que deben leerse. Si cada llamada a [lectura](#read) normalmente implica una aount grande de datos (por ejemplo, cuatro o más kilobytes), no es necesario un búfer. Sin embargo, si se llama a `Read` obtener pequeños fragmentos de datos, o si usa [ReadString](#readstring) para leer las líneas individuales a la vez, un búfer de lectura mejora el rendimiento de la aplicación.  
  
 De forma predeterminada, un `CInternetFile` objeto no proporciona ningún almacenamiento en búfer para su lectura. Si se llama a esta función miembro, debe asegurarse de que el archivo se ha abierto para acceso de lectura.  
  
 Puede aumentar el tamaño del búfer en cualquier momento, pero el búfer de la reducción no tendrá ningún efecto. Si se llama a [ReadString](#readstring) sin llamar primero a `SetReadBufferSize`, obtendrá un búfer de 4096 bytes.  
  
##  <a name="setwritebuffersize"></a>  CInternetFile::SetWriteBufferSize  
 Llame a esta función miembro para establecer el tamaño del búfer de escritura temporal usado por un `CInternetFile`-objeto derivado.  
  
```  
BOOL SetWriteBufferSize(UINT nWriteSize);
```  
  
### <a name="parameters"></a>Parámetros  
 *nWriteSize*  
 El tamaño del búfer en bytes.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, la función de Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) puede llamarse para determinar la causa del error.  
  
### <a name="remarks"></a>Comentarios  
 Subyacente WinInet APIs no realiza el almacenamiento en búfer, por lo que se elija un tamaño de búfer que permite que la aplicación escribir datos de manera eficiente, independientemente de la cantidad de datos se escriban. Si cada llamada a [escribir](#write) normalmente implica una gran cantidad de datos (por ejemplo, cuatro o más kilobytes a la vez), no es necesario un búfer. Sin embargo, si se llama a [escribir](#write) para escribir pequeños fragmentos de datos, un búfer de escritura mejora el rendimiento de la aplicación.  
  
 De forma predeterminada, un `CInternetFile` objeto no proporciona ningún almacenamiento en búfer para escribir en él. Si se llama a esta función miembro, debe asegurarse de que el archivo se ha abierto para acceso de escritura. Puede cambiar el tamaño del búfer de escritura en cualquier momento, pero si lo hace una llamada implícita a [vaciar](#flush).  
  
##  <a name="write"></a>  CInternetFile:: Write  
 Llame a esta función miembro para escribir en la memoria determinada, *lpvBuf*, el número especificado de bytes, *nCount*.  
  
```  
virtual void Write(
    const void* lpBuf,  
    UINT nCount);
```  
  
### <a name="parameters"></a>Parámetros  
 *lpBuf*  
 Un puntero al primer byte que se va a escribir.  
  
 *nCount*  
 Especifica el número de bytes que se escribirán.  
  
### <a name="remarks"></a>Comentarios  
 Si se produce un error al escribir los datos, la función produce un [CInternetException](../../mfc/reference/cinternetexception-class.md) objeto que describe el error.  
  
##  <a name="writestring"></a>  CInternetFile::WriteString  
 Esta función escribe una cadena terminada en null en el archivo asociado.  
  
```  
virtual void WriteString(LPCTSTR pstr);
```  
  
### <a name="parameters"></a>Parámetros  
 *pStr*  
 Un puntero a una cadena que contiene el contenido que se va a escribir.  
  
### <a name="remarks"></a>Comentarios  
 Si se produce un error al escribir los datos, la función produce un [CInternetException](../../mfc/reference/cinternetexception-class.md) objeto que describe el error.  
  
## <a name="see-also"></a>Vea también  
 [CStdioFile (clase)](../../mfc/reference/cstdiofile-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CInternetConnection (clase)](../../mfc/reference/cinternetconnection-class.md)
