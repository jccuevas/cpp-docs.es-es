---
title: Clase CStdioFile | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CStdioFile
- AFX/CStdioFile
- AFX/CStdioFile::CStdioFile
- AFX/CStdioFile::Open
- AFX/CStdioFile::ReadString
- AFX/CStdioFile::Seek
- AFX/CStdioFile::WriteString
- AFX/CStdioFile::m_pStream
dev_langs:
- C++
helpviewer_keywords:
- CStdioFile class
- I/O [MFC], stream
- stream I/O
ms.assetid: 88c2274c-4f0e-4327-882a-557ba4b3ae15
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
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: 6b334c2973a2567a8a9bd16a80bd4c3628ced6d2
ms.lasthandoff: 04/01/2017

---
# <a name="cstdiofile-class"></a>Clase CStdioFile
Representa un archivo de secuencia de tiempo de ejecución de C tal como lo abre la función en tiempo de ejecución [fopen](../../c-runtime-library/reference/fopen-wfopen.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CStdioFile : public CFile  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CStdioFile::CStdioFile](#cstdiofile)|Construye un `CStdioFile` objeto de un puntero de archivo o ruta de acceso.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CStdioFile::Open](#open)|Sobrecargado. Abrir está diseñado para su uso con el valor predeterminado `CStdioFile` constructor (reemplaza a [CFile::Open](../../mfc/reference/cfile-class.md#open)).|  
|[CStdioFile::ReadString](#readstring)|Lee una sola línea de texto.|  
|[CStdioFile::Seek](#seek)|Coloca el puntero de archivo actual.|  
|[CStdioFile::WriteString](#writestring)|Escribe una sola línea de texto.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CStdioFile::m_pStream](#m_pstream)|Contiene un puntero a un archivo abierto.|  
  
## <a name="remarks"></a>Comentarios  
 Archivos de flujo se almacenan en búfer y se pueden abrir en modo de texto (el valor predeterminado) o modo binario.  
  
 Modo de texto proporciona un procesamiento especial para los pares de avance de línea de retorno de carro. Al escribir una nueva línea (0x0A) de caracteres a un modo de texto `CStdioFile` (objeto), el par de bytes (0x0D, 0x0A) se envía al archivo. Al leer, el par de bytes (0x0D, 0x0A) se traduce en un solo byte 0x0A.  
  
 El [CFile](../../mfc/reference/cfile-class.md) funciones [duplicar](../../mfc/reference/cfile-class.md#duplicate), [LockRange](../../mfc/reference/cfile-class.md#lockrange), y [UnlockRange](../../mfc/reference/cfile-class.md#unlockrange) no son compatibles con `CStdioFile`.  
  
 Si se llama a estas funciones en un `CStdioFile`, obtendrá un [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).  
  
 Para obtener más información sobre el uso de `CStdioFile`, consulte los artículos [archivos en MFC](../../mfc/files-in-mfc.md) y [archivo control](../../c-runtime-library/file-handling.md) en el *referencia de la biblioteca de tiempo de ejecución*.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 `CStdioFile`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h  
  
##  <a name="cstdiofile"></a>CStdioFile::CStdioFile  
 Construye e inicializa un objeto `CStdioFile`.  
  
```  
CStdioFile();  
CStdioFile(CAtlTransactionManager* pTM);  
  CStdioFile(FILE* pOpenStream);

 
CStdioFile(
    LPCTSTR lpszFileName,  
    UINT nOpenFlags);

 
CStdioFile(
    LPCTSTR lpszFileName,
    UINT nOpenFlags,
    CAtlTransactionManager* pTM);
```  
  
### <a name="parameters"></a>Parámetros  
 `pOpenStream`  
 Especifica el puntero de archivo devuelto por una llamada a la función de tiempo de ejecución de C [fopen](../../c-runtime-library/reference/fopen-wfopen.md).  
  
 `lpszFileName`  
 Especifica una cadena que es la ruta de acceso al archivo deseado. La ruta de acceso puede ser absoluta o relativa.  
  
 `nOpenFlags`  
 Especifica las opciones de creación de archivo, uso compartido de archivos y los modos de acceso de archivo. Puede especificar varias opciones mediante la operación OR bit a bit ( `|`) operador.  
  
 Una opción de modo de acceso de archivo es necesaria; otros modos son opcionales. Vea [CFile::CFile](../../mfc/reference/cfile-class.md#cfile) para obtener una lista de opciones del modo y otros indicadores. En la versión 3.0 y versiones posterior de MFC, se permiten marcas de recurso compartido.  
  
 `pTM`  
 Puntero al objeto CAtlTransactionManager.  
  
### <a name="remarks"></a>Comentarios  
 El constructor predeterminado no adjunta un archivo a la `CStdioFile` objeto. Al utilizar este constructor, debe utilizar el `CStdioFile::Open` método para abrir un archivo y adjuntarla a la `CStdioFile` objeto.  
  
 El único parámetro constructor asocia un flujo de archivos abiertos en el `CStdioFile` objeto. Permite a los valores de puntero incluyen los punteros a archivos de entrada/salida predefinidos `stdin`, `stdout`, o `stderr`.  
  
 El constructor de dos parámetros crea una `CStdioFile` de objetos y abre el archivo correspondiente con la ruta de acceso especificada.  
  
 Si se pasa `NULL` para cada uno `pOpenStream` o `lpszFileName`, el constructor produce una `CInvalidArgException*`.  
  
 Si el archivo no se abre o se crea, el constructor produce una `CFileException*`.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCFiles #37](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_1.cpp)]  
  
##  <a name="m_pstream"></a>CStdioFile::m_pStream  
 El `m_pStream` miembro de datos es el puntero a un archivo abierto, tal como lo devuelve la función de tiempo de ejecución de C `fopen`.  
  
```  
FILE* m_pStream;  
```  
  
### <a name="remarks"></a>Comentarios  
 Es **NULL** si el archivo no se ha abierto nunca o se ha cerrado.  
  
##  <a name="open"></a>CStdioFile::Open  
 Sobrecargado. Abrir está diseñado para su uso con el valor predeterminado `CStdioFile` constructor.  
  
```  
virtual BOOL Open(
    LPCTSTR lpszFileName,  
    UINT nOpenFlags,  
    CFileException* pError = NULL);

 
virtual BOOL Open(
    LPCTSTR lpszFileName,  
    UINT nOpenFlags,  
    CAtlTransactionManager* pTM,  
    CFileException* pError = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszFileName`  
 Una cadena que es la ruta de acceso al archivo deseado. La ruta de acceso puede ser absoluta o relativa.  
  
 `nOpenFlags`  
 Modo de acceso y uso compartido. Especifica la acción que se realizará al abrir el archivo. Puede combinar opciones mediante el operador OR bit a bit (|). Permiso de acceso uno a y opción de un recurso compartido son necesarios; los modos modeCreate y modeNoInherit son opcionales.  
  
 `pError`  
 Un puntero a un objeto de excepción de archivo existente que va a recibir el estado de una operación con errores.  
  
 `pTM`  
 Puntero a un `CAtlTransactionManager` objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE` si es correcto; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="readstring"></a>CStdioFile::ReadString  
 Lee datos de texto en un búfer, hasta un límite de `nMax`-1 caracteres, desde el archivo asociado a la `CStdioFile` objeto.  
  
```  
virtual LPTSTR ReadString(
    LPTSTR lpsz,  
    UINT nMax);  
  
virtual BOOL ReadString(CString& rString);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpsz`  
 Especifica un puntero a un búfer proporcionado por el usuario que va a recibir una cadena de texto terminada en null.  
  
 `nMax`  
 Especifica el número máximo de caracteres que se va a leer, sin contar el carácter nulo de terminación.  
  
 `rString`  
 Una referencia a un `CString` objeto que va a contener la cadena cuando la función devuelve.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al búfer que contiene los datos de texto. **NULL** si se alcanza el final de archivo sin necesidad de leer los datos; o booleano, **FALSE** si se alcanza el final de archivo sin necesidad de leer los datos.  
  
### <a name="remarks"></a>Comentarios  
 Lectura se ha detenido por el primer carácter de nueva línea. Si, en ese caso, menos de `nMax`se han leído-1 caracteres, un carácter de nueva línea se almacena en el búfer. En cualquier caso, se anexa un carácter nulo ('\0').  
  
 [CFile:: Read](../../mfc/reference/cfile-class.md#read) también está disponible para los datos proporcionados por modo de texto, pero no termina en un par de retorno de carro.  
  
> [!NOTE]
>  El `CString` versión de esta función quita el `'\n'` si está presente; la `LPTSTR` versión no lo hace.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCFiles #38](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_2.cpp)]  
  
##  <a name="seek"></a>CStdioFile::Seek  
 Cambia de posición el puntero en un archivo abierto anteriormente.  
  
```  
virtual ULONGLONG Seek(
    LONGLONG lOff,  
    UINT nFrom);
```  
  
### <a name="parameters"></a>Parámetros  
 `lOff`  
 Número de bytes que se va a mover el puntero.  
  
 `nFrom`  
 Modo de movimiento del puntero. Debe ser uno de los siguientes valores:  
  
- `CFile::begin`: Mueva el puntero de archivo `lOff` reenvían bytes desde el principio del archivo.  
  
- `CFile::current`: Mueva el puntero de archivo `lOff` bytes desde la posición actual en el archivo.  
  
- `CFile::end`: Mueva el puntero de archivo `lOff` bytes desde el final del archivo. Tenga en cuenta que `lOff` debe negativo para buscar en las existentes de archivos; positivo buscarán valores más allá del final del archivo.  
  
### <a name="return-value"></a>Valor devuelto  
 Si la posición solicitada es válida, `Seek` devuelve el desplazamiento de bytes de nuevo desde el principio del archivo. En caso contrario, el valor devuelto es indefinido y un `CFileException` se produce el objeto.  
  
### <a name="remarks"></a>Comentarios  
 El `Seek` función permite el acceso aleatorio al contenido de un archivo, mueva el puntero una cantidad especificada, absoluta o relativa. En realidad se leerá ningún dato durante la búsqueda. Si la posición solicitada es mayor que el tamaño del archivo, la longitud del archivo se extenderá a esa posición y no se producirá ninguna excepción.  
  
 Cuando se abre un archivo, se coloca el puntero de archivo con un desplazamiento 0, el principio del archivo.  
  
 Esta implementación de `Seek` se basa en la función de biblioteca en tiempo de ejecución (CRT) `fseek`. Existen varios límites para el uso de `Seek` en flujos abiertos en modo de texto. Para obtener más información, consulte [fseek, _fseeki64](../../c-runtime-library/reference/fseek-fseeki64.md).  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo usar `Seek` para mover el puntero 1000 bytes desde el principio de la `cfile` archivo. Tenga en cuenta que `Seek` no leer los datos, por lo que debe llamar posteriormente [CStdioFile::ReadString](#readstring) para leer los datos.  
  
 [!code-cpp[NVC_MFCFiles #39](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_3.cpp)]  
  
##  <a name="writestring"></a>CStdioFile::WriteString  
 Escribe datos de un búfer en el archivo asociado a la `CStdioFile` objeto.  
  
```  
virtual void WriteString(LPCTSTR lpsz);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpsz`  
 Especifica un puntero a un búfer que contiene una cadena terminada en null.  
  
### <a name="remarks"></a>Comentarios  
 El carácter nulo de terminación ( `\0`) no se escribe en el archivo. Este método escribe caracteres de nueva línea `lpsz` el archivo como un par de carro/avance de línea de retorno.  
  
 Si desea escribir los datos que no está terminada en null en un archivo, use `CStdioFile::Write` o [CFile::Write](../../mfc/reference/cfile-class.md#write).  
  
 Este método produce una `CInvalidArgException*` si especifica `NULL` para el `lpsz` parámetro.  
  
 Este método produce una `CFileException*` en respuesta a errores de sistema de archivos.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCFiles Nº 40](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_4.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [CFile (clase)](../../mfc/reference/cfile-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CFile (clase)](../../mfc/reference/cfile-class.md)   
 [CFile::Duplicate](../../mfc/reference/cfile-class.md#duplicate)   
 [CFile::LockRange](../../mfc/reference/cfile-class.md#lockrange)   
 [CFile::UnlockRange](../../mfc/reference/cfile-class.md#unlockrange)   
 [CNotSupportedException (clase)](../../mfc/reference/cnotsupportedexception-class.md)

