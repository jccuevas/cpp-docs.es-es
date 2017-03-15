---
title: Clase de CInternetFile | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CInternetFile
dev_langs:
- C++
helpviewer_keywords:
- CInternetFile class
- Internet files
- Internet files, CInternetFile class
ms.assetid: 96935681-ee71-4a8d-9783-5abc7b3e6f10
caps.latest.revision: 23
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
ms.openlocfilehash: 6e1d6227ebd642025e6b00019518d29080cf0454
ms.lasthandoff: 02/24/2017

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
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CInternetFile::Abort](#abort)|Cierra el archivo, omitiendo todos los errores y advertencias.|  
|[CInternetFile::Close](#close)|Cierra un `CInternetFile` y libera sus recursos.|  
|[CInternetFile::Flush](#flush)|Vuelca el contenido del búfer de escritura y se asegura de que los datos en memoria se escriben en el equipo de destino.|  
|[CInternetFile::GetLength](#getlength)|Devuelve el tamaño del archivo.|  
|[CInternetFile:: Read](#read)|Lee el número de bytes especificados.|  
|[CInternetFile::ReadString](#readstring)|Lee una secuencia de caracteres.|  
|[CInternetFile::Seek](#seek)|Cambia de posición el puntero en un archivo abierto.|  
|[CInternetFile::SetReadBufferSize](#setreadbuffersize)|Establece el tamaño del búfer donde se leerán los datos.|  
|[CInternetFile::SetWriteBufferSize](#setwritebuffersize)|Establece el tamaño del búfer donde se escribirán datos.|  
|[CInternetFile:: Write](#write)|Escribe el número de bytes especificados.|  
|[CInternetFile::WriteString](#writestring)|Escribe una cadena terminada en null en un archivo.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CInternetFile::operator HINTERNET](#operator_hinternet)|Un operador de conversión para un identificador de Internet.|  
  
### <a name="protected-data-members"></a>Miembros de datos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CInternetFile::m_hFile](#m_hfile)|Un identificador a un archivo.|  
  
## <a name="remarks"></a>Comentarios  
 Proporciona una clase base para la [CHttpFile](../../mfc/reference/chttpfile-class.md) y [CGopherFile](../../mfc/reference/cgopherfile-class.md) clases de archivos. No cree nunca un `CInternetFile` objeto directamente. En su lugar, cree un objeto de uno de sus clases derivadas llamando a [CGopherConnection:: OpenFile](../../mfc/reference/cgopherconnection-class.md#openfile) o [CHttpConnection:: OpenRequest](../../mfc/reference/chttpconnection-class.md#openrequest). También puede crear un `CInternetFile` objeto mediante una llamada a [CFtpConnection:: OpenFile](../../mfc/reference/cftpconnection-class.md#openfile).  
  
 El `CInternetFile` funciones miembro **abiertos**, `LockRange`, `UnlockRange`, y `Duplicate` no se implementan para `CInternetFile`. Si se llama a estas funciones en una `CInternetFile` objeto, obtendrá un [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).  
  
 Para obtener más información acerca de cómo `CInternetFile` funciona con otras clases de Internet de MFC, vea el artículo [programación para Internet con WinInet](../../mfc/win32-internet-extensions-wininet.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 [CStdioFile](../../mfc/reference/cstdiofile-class.md)  
  
 `CInternetFile`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxinet.h  
  
##  <a name="a-nameaborta--cinternetfileabort"></a><a name="abort"></a>CInternetFile::Abort  
 Cierra el archivo asociado a este objeto y hace que el archivo no esté disponible para lectura o escritura.  
  
```  
virtual void Abort();
```  
  
### <a name="remarks"></a>Comentarios  
 Si no ha cerrado el archivo antes de destruir el objeto, el destructor cierra automáticamente.  
  
 Cuando el control de excepciones, **anular** difiere de [cerrar](#close) en dos aspectos importantes. En primer lugar, el **anular** función no produce una excepción en errores porque omite los errores. Segundo, **anular** no **ASSERT** si el archivo no se abrió o se ha cerrado previamente.  
  
##  <a name="a-namecinternetfilea--cinternetfilecinternetfile"></a><a name="cinternetfile"></a>CInternetFile::CInternetFile  
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
 `hFile`  
 Identificador de un archivo de Internet.  
  
 `pstrFileName`  
 Un puntero a una cadena que contiene el nombre de archivo.  
  
 `pConnection`  
 Un puntero a un [CInternetConnection](../../mfc/reference/cinternetconnection-class.md) objeto.  
  
 *bReadMode*  
 Indica si el archivo es de sólo lectura.  
  
 `hSession`  
 Identificador de sesión de Internet.  
  
 `pstrServer`  
 Un puntero a una cadena que contiene el nombre del servidor.  
  
 `dwContext`  
 El identificador de contexto para la `CInternetFile` objeto. Consulte [Fundamentos de WinInet](../../mfc/wininet-basics.md) para obtener más información sobre el identificador de contexto.  
  
### <a name="remarks"></a>Comentarios  
 No cree nunca un `CInternetFile` objeto directamente. En su lugar, cree un objeto de uno de sus clases derivadas llamando a [CGopherConnection:: OpenFile](../../mfc/reference/cgopherconnection-class.md#openfile) o [CHttpConnection:: OpenRequest](../../mfc/reference/chttpconnection-class.md#openrequest). También puede crear un `CInternetFile` objeto mediante una llamada a [CFtpConnection:: OpenFile](../../mfc/reference/cftpconnection-class.md#openfile).  
  
##  <a name="a-nameclosea--cinternetfileclose"></a><a name="close"></a>CInternetFile::Close  
 Cierra un `CInternetFile` y libera sus recursos.  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>Comentarios  
 Si el archivo se abre para escritura, hay una llamada implícita a [vaciar](#flush) para asegurarse de que todos los datos almacenados en búfer se escriban en el host. Debe llamar a **cerrar** cuando haya terminado de usar un archivo.  
  
##  <a name="a-nameflusha--cinternetfileflush"></a><a name="flush"></a>CInternetFile::Flush  
 Llame a esta función miembro para vaciar el contenido del búfer de escritura.  
  
```  
virtual void Flush();
```  
  
### <a name="remarks"></a>Comentarios  
 Use `Flush` para asegurarse de que todos los datos en la memoria se ha escrito realmente en el equipo de destino y para asegurarse de que se ha completado la transacción con el equipo host. `Flush`sólo es efectivo en `CInternetFile` objetos abrir para escritura.  
  
##  <a name="a-namegetlengtha--cinternetfilegetlength"></a><a name="getlength"></a>CInternetFile::GetLength  
 Devuelve el tamaño del archivo.  
  
```  
virtual ULONGLONG GetLength() const;  
```  
  
##  <a name="a-namemhfilea--cinternetfilemhfile"></a><a name="m_hfile"></a>CInternetFile::m_hFile  
 Un identificador para el archivo asociado a este objeto.  
  
```  
HINTERNET m_hFile;  
```  
  
##  <a name="a-nameoperatorhinterneta--cinternetfileoperator-hinternet"></a><a name="operator_hinternet"></a>CInternetFile::operator HINTERNET  
 Utilice este operador para obtener el identificador de Windows para la sesión actual de Internet.  
  
```  
operator HINTERNET() const;  
```  
  
##  <a name="a-namereada--cinternetfileread"></a><a name="read"></a>CInternetFile:: Read  
 Llame a esta función miembro para leer en la memoria determinada, comenzando en `lpvBuf`, el número especificado de bytes, `nCount`.  
  
```  
virtual UINT Read(
    void* lpBuf,  
    UINT nCount);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpBuf`  
 Puntero a una dirección de memoria para la que se leen datos de archivo.  
  
 `nCount`  
 Número de bytes que se escribirán.  
  
### <a name="return-value"></a>Valor devuelto  
 Número de bytes que se transfieren al búfer. El valor devuelto puede ser menor que `nCount` si se alcanzó el final del archivo.  
  
### <a name="remarks"></a>Comentarios  
 La función devuelve el número de bytes que se leyeron realmente (número que puede ser menor que `nCount` si el archivo finaliza). Si se produce un error al leer el archivo, la función produce una [clase CInternetException](../../mfc/reference/cinternetexception-class.md) objeto que describe el error. Tenga en cuenta que leer más allá del final del archivo no se considera un error y no se generará ninguna excepción.  
  
 Para asegurarse de que se recuperan todos los datos, una aplicación debe seguir llamar a la **CInternetFile:: Read** método hasta que el método devuelve cero.  
  
##  <a name="a-namereadstringa--cinternetfilereadstring"></a><a name="readstring"></a>CInternetFile::ReadString  
 Llame a esta función miembro para leer una secuencia de caracteres hasta que encuentra un carácter de nueva línea.  
  
```  
virtual BOOL ReadString(CString& rString);

 
virtual LPTSTR ReadString(
    LPTSTR pstr,  
    UINT nMax);
```  
  
### <a name="parameters"></a>Parámetros  
 `pstr`  
 Un puntero a una cadena que recibirá la línea que se va a leer.  
  
 `nMax`  
 El número máximo de caracteres que leer.  
  
 `rString`  
 Una referencia a la [CString](../../atl-mfc-shared/reference/cstringt-class.md) objeto que recibe la línea de lectura.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al búfer que contiene los datos sin formato que se recuperan de la [CInternetFile](../../mfc/reference/cinternetfile-class.md) objeto. Independientemente del tipo de datos del búfer pasado a este método, no realiza las manipulaciones de los datos (por ejemplo, la conversión a Unicode), por lo que debe asignar los datos devueltos a la estructura de espera, como si la **void\* ** devolvió el tipo.  
  
 **NULL** si se alcanzó el final de archivo sin necesidad de leer los datos; o bien, si es booleano, **FALSE** si se alcanzó el final de archivo sin necesidad de leer los datos.  
  
### <a name="remarks"></a>Comentarios  
 La función coloca la línea resultante en la memoria al que hace referencia el `pstr` parámetro. Deja de leer caracteres cuando alcanza el número máximo de caracteres, especificado por `nMax`. El búfer recibe siempre un carácter nulo de terminación.  
  
 Si se llama a `ReadString` sin llamar primero a [SetReadBufferSize](#setreadbuffersize), obtendrá un búfer de 4096 bytes.  
  
##  <a name="a-nameseeka--cinternetfileseek"></a><a name="seek"></a>CInternetFile::Seek  
 Llame a esta función miembro para colocar el puntero en un archivo abierto anteriormente.  
  
```  
virtual ULONGLONG Seek(
    LONGLONG lOffset,  
    UINT nFrom);
```  
  
### <a name="parameters"></a>Parámetros  
 `lOffset`  
 Desplazamiento en bytes para mover el puntero de lectura y escritura en el archivo.  
  
 `nFrom`  
 Referencia relativa para el desplazamiento. Debe ser uno de los siguientes valores:  
  
- **CFile::begin** mover el puntero de archivo `lOff` reenvían bytes desde el principio del archivo.  
  
- **CFile::current** mover el puntero de archivo `lOff` bytes desde la posición actual en el archivo.  
  
- **CFile::end** mover el puntero de archivo `lOff` bytes desde el final del archivo. `lOff`debe ser negativo para buscar en el archivo existente; los valores positivos realizará una búsqueda más allá del final del archivo.  
  
### <a name="return-value"></a>Valor devuelto  
 El nuevo desplazamiento de bytes desde el principio del archivo si la posición solicitada es legal; de lo contrario, el valor es indefinido y un [clase CInternetException](../../mfc/reference/cinternetexception-class.md) se inicia el objeto.  
  
### <a name="remarks"></a>Comentarios  
 El `Seek` función permite el acceso aleatorio al contenido de un archivo, mueva el puntero una cantidad especificada, absoluta o relativa. En realidad se leerá ningún dato durante la búsqueda.  
  
 En este momento, sólo se admite una llamada a esta función miembro de los datos asociados con `CHttpFile` objetos. No se admite para las solicitudes FTP o gopher. Si se llama a `Seek` en uno de estos servicios no compatibles, pasará vuelve al código de error Win32 **ERROR_INTERNET_INVALID_OPERATION**.  
  
 Cuando se abre un archivo, es el puntero de archivo en el desplazamiento 0, el principio del archivo.  
  
> [!NOTE]
>  Usando `Seek` puede provocar una llamada implícita a [vaciar](#flush).  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de implementación de la clase base ( [CFile::Seek](../../mfc/reference/cfile-class.md#seek)).  
  
##  <a name="a-namesetreadbuffersizea--cinternetfilesetreadbuffersize"></a><a name="setreadbuffersize"></a>CInternetFile::SetReadBufferSize  
 Llame a esta función miembro para establecer el tamaño del búfer de lectura temporal utilizado por un `CInternetFile`-objeto derivado.  
  
```  
BOOL SetReadBufferSize(UINT nReadSize);
```  
  
### <a name="parameters"></a>Parámetros  
 *nReadSize*  
 Tamaño deseado del búfer en bytes.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, la función de Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) puede llamar para determinar la causa del error.  
  
### <a name="remarks"></a>Comentarios  
 Las APIs WinInet subyacente no realizar el almacenamiento en búfer, elija un tamaño de búfer que permite a la aplicación leer los datos de manera eficaz, independientemente de la cantidad de datos que deben leerse. Si cada llamada a [lectura](#read) normalmente implica una aount grande de datos (por ejemplo, cuatro o más kilobytes), no es necesario un búfer. Sin embargo, si se llama a **lectura** obtener pequeños bloques de datos, o si usa [ReadString](#readstring) para leer las líneas individuales en un momento, un búfer de lectura mejora el rendimiento de la aplicación.  
  
 De forma predeterminada, un `CInternetFile` objeto no proporciona ningún almacenamiento en búfer para su lectura. Si se llama a esta función miembro, debe asegurarse de que el archivo se ha abierto para acceso de lectura.  
  
 Puede aumentar el tamaño del búfer en cualquier momento, pero reducir el búfer no tiene ningún efecto. Si se llama a [ReadString](#readstring) sin llamar primero a `SetReadBufferSize`, obtendrá un búfer de 4096 bytes.  
  
##  <a name="a-namesetwritebuffersizea--cinternetfilesetwritebuffersize"></a><a name="setwritebuffersize"></a>CInternetFile::SetWriteBufferSize  
 Llame a esta función miembro para establecer el tamaño del búfer de escritura temporal utilizado por un `CInternetFile`-objeto derivado.  
  
```  
BOOL SetWriteBufferSize(UINT nWriteSize);
```  
  
### <a name="parameters"></a>Parámetros  
 *nWriteSize*  
 El tamaño del búfer en bytes.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, la función de Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) puede llamar para determinar la causa del error.  
  
### <a name="remarks"></a>Comentarios  
 Así se subyacente WinInet APIs no realiza el almacenamiento en búfer, elija un tamaño de búfer que permite a su aplicación para escribir datos eficazmente, independientemente de la cantidad de datos que se va a escribir. Si cada llamada a [escribir](#write) normalmente implica una gran cantidad de datos (por ejemplo, cuatro o más kilobytes a la vez), no es necesario un búfer. Sin embargo, si se llama a [escribir](#write) para escribir pequeños bloques de datos, un búfer de escritura mejora el rendimiento de la aplicación.  
  
 De forma predeterminada, un `CInternetFile` objeto no proporciona ningún almacenamiento en búfer para escribir en él. Si se llama a esta función miembro, debe asegurarse de que el archivo se ha abierto para acceso de escritura. Puede cambiar el tamaño del búfer de escritura en cualquier momento, pero si lo hace una llamada implícita a [vaciar](#flush).  
  
##  <a name="a-namewritea--cinternetfilewrite"></a><a name="write"></a>CInternetFile:: Write  
 Llame a esta función miembro para escribir en la memoria dada, `lpvBuf`, el número especificado de bytes, `nCount`.  
  
```  
virtual void Write(
    const void* lpBuf,  
    UINT nCount);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpBuf`  
 Un puntero al primer byte que se va a escribir.  
  
 `nCount`  
 Especifica el número de bytes que se escribirán.  
  
### <a name="remarks"></a>Comentarios  
 Si se produce un error al escribir los datos, la función produce una [clase CInternetException](../../mfc/reference/cinternetexception-class.md) objeto que describe el error.  
  
##  <a name="a-namewritestringa--cinternetfilewritestring"></a><a name="writestring"></a>CInternetFile::WriteString  
 Esta función escribe una cadena terminada en null en el archivo asociado.  
  
```  
virtual void WriteString(LPCTSTR pstr);
```  
  
### <a name="parameters"></a>Parámetros  
 `pstr`  
 Puntero a una cadena que contiene el contenido que se va a escribir.  
  
### <a name="remarks"></a>Comentarios  
 Si se produce un error al escribir los datos, la función produce una [clase CInternetException](../../mfc/reference/cinternetexception-class.md) objeto que describe el error.  
  
## <a name="see-also"></a>Vea también  
 [Clase CStdioFile](../../mfc/reference/cstdiofile-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [CInternetConnection (clase)](../../mfc/reference/cinternetconnection-class.md)

