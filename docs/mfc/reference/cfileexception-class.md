---
title: Clase CFileException | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CFileException
- AFX/CFileException
- AFX/CFileException::CFileException
- AFX/CFileException::ErrnoToException
- AFX/CFileException::GetErrorMessage
- AFX/CFileException::OsErrorToException
- AFX/CFileException::ThrowErrno
- AFX/CFileException::ThrowOsError
- AFX/CFileException::m_cause
- AFX/CFileException::m_lOsError
- AFX/CFileException::m_strFileName
dev_langs:
- C++
helpviewer_keywords:
- CFile class, exceptions of
- exceptions, file type
- CFileException class
ms.assetid: f6491bb9-bfbc-42fd-a952-b33f9b62323f
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: d9064ae66f0dcd0e9f0dce0eedd8e38353f9da06
ms.lasthandoff: 02/24/2017

---
# <a name="cfileexception-class"></a>CFileException (clase)
Representa una condición de excepción relacionada con archivo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CFileException : public CException  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CFileException::CFileException](#cfileexception)|Construye un objeto `CFileException`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CFileException::ErrnoToException](#errnotoexception)|Devuelve que el código correspondiente a un número de error de tiempo de ejecución.|  
|[CFileException::GetErrorMessage](#geterrormessage)|Recupera el mensaje que describe una excepción.|  
|[CFileException::OsErrorToException](#oserrortoexception)|Devuelve un código de causa correspondiente a un código de error del sistema operativo.|  
|[CFileException::ThrowErrno](#throwerrno)|Produce una excepción de archivo basada en un número de error en tiempo de ejecución.|  
|[CFileException::ThrowOsError](#throwoserror)|Produce una excepción de archivo basada en un número de error del sistema operativo.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CFileException::m_cause](#m_cause)|Contiene código portable correspondiente a la causa de la excepción.|  
|[CFileException::m_lOsError](#m_loserror)|Contiene el número de errores del sistema operativo relacionados.|  
|[CFileException::m_strFileName](#m_strfilename)|Contiene el nombre del archivo para esta excepción.|  
  
## <a name="remarks"></a>Comentarios  
 La `CFileException` clase incluye miembros de datos públicos que contienen el código portable causa y el número de error específicos del sistema operativo. La clase también proporciona funciones miembro estáticas para producir excepciones de archivo y para devolver los códigos de causa de errores de sistema operativo y errores de tiempo de ejecución de C.  
  
 `CFileException`los objetos se construyen y se produce en `CFile` funciones miembro y en las funciones miembro de clases derivadas. Puede tener acceso a estos objetos dentro del ámbito de un **CATCH** expresión. Para la portabilidad, utilice el código de la causa para obtener el motivo de una excepción. Para obtener más información sobre las excepciones, vea el artículo [de control de excepciones (MFC)](../../mfc/exception-handling-in-mfc.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 `CFileException`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h  
  
##  <a name="cfileexception"></a>CFileException::CFileException  
 Construye un `CFileException` objeto que almacena el código de la causa y el código del sistema operativo en el objeto.  
  
```  
CFileException(
    int cause = CFileException::none,  
    LONG lOsError = -1,  
    LPCTSTR lpszArchiveName = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `cause`  
 Una variable de tipo enumerado que indica el motivo de la excepción. Consulte [CFileException::m_cause](#m_cause) para obtener una lista de los valores posibles.  
  
 `lOsError`  
 Un motivo específicos del sistema operativo para la excepción, si está disponible. El `lOsError` parámetro proporciona más información que `cause` does.  
  
 `lpszArchiveName`  
 Señala a una cadena que contiene el nombre de la `CFile` objeto ocasionando la excepción.  
  
### <a name="remarks"></a>Comentarios  
 No utilice este constructor directamente, pero en su lugar llame a la función global [AfxThrowFileException](exception-processing.md#afxthrowfileexception).  
  
> [!NOTE]
>  La variable `lOsError` sólo se aplica a `CFile` y `CStdioFile` objetos. La `CMemFile` clase no controla este código de error.  
  
##  <a name="errnotoexception"></a>CFileException::ErrnoToException  
 Convierte un valor de error de la biblioteca de tiempo de ejecución concreta en un `CFileException` el valor de error enumerado.  
  
```  
static int PASCAL ErrnoToException(int nErrno);
```  
  
### <a name="parameters"></a>Parámetros  
 `nErrno`  
 Código de error entero como se define en el archivo de inclusión de tiempo de ejecución ERRNO. H.  
  
### <a name="return-value"></a>Valor devuelto  
 Valor enumerado que corresponde a un valor de error de la biblioteca de tiempo de ejecución concreta.  
  
### <a name="remarks"></a>Comentarios  
 Consulte [CFileException::m_cause](#m_cause) para obtener una lista de los posibles valores enumerados.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[26 de NVC_MFCFiles #](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_1.cpp)]  
  
##  <a name="geterrormessage"></a>CFileException::GetErrorMessage  
 Recupera el texto que describe una excepción.  
  
```  
virtual BOOL GetErrorMessage(
    LPTSTR lpszError,  
    UINT nMaxError,  
    PUINT pnHelpContext = NULL) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in, out] `lpszError`  
 Puntero a un búfer que recibe un mensaje de error.  
  
 [in] `nMaxError`  
 El número máximo de caracteres que puede contener el búfer especificado. Esto incluye el carácter nulo de terminación.  
  
 [in, out] `pnHelpContext`  
 Puntero a un entero sin signo que recibe el identificador de contexto de ayuda. Si `NULL`, no se devuelve ningún ID.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el método se realizó correctamente; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Si el búfer especificado es demasiado pequeño, se trunca el mensaje de error.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se utiliza `CFileException::GetErrorMessage`.  
  
 [!code-cpp[NVC_MFCExceptions&#22;](../../mfc/codesnippet/cpp/cfileexception-class_2.cpp)]  
  
##  <a name="m_cause"></a>CFileException::m_cause  
 Contiene los valores definidos por un tipo enumerado `CFileException`.  
  
```  
int m_cause;  
```  
  
### <a name="remarks"></a>Comentarios  
 Este miembro de datos es una variable pública de tipo `int`. A continuación se indican los enumeradores y el significado de cada uno de ellos:  
  
- `CFileException::none`0: se produjo ningún error.  
  
- `CFileException::genericException`1: se produjo un error no especificado.  
  
- `CFileException::fileNotFound`2: no se pudo encontrar el archivo.  
  
- `CFileException::badPath`3: todo o parte de la ruta de acceso no es válido.  
  
- `CFileException::tooManyOpenFiles`4: se superó el número permitido de archivos abiertos.  
  
- `CFileException::accessDenied`5: no se pudo acceder al archivo.  
  
- `CFileException::invalidFile`6: se produjo un intento de usar un identificador de archivo no válido.  
  
- `CFileException::removeCurrentDir`7: no se puede quitar el directorio de trabajo actual.  
  
- `CFileException::directoryFull`8: no existen más entradas de directorio.  
  
- `CFileException::badSeek`9: se produjo un error al intentar establecer el puntero de archivo.  
  
- `CFileException::hardIO`10: se produjo un error de hardware.  
  
- `CFileException::sharingViolation`11: RECURSO COMPARTIDO. No se ha cargado el archivo EXE o una región compartida estaba bloqueada.  
  
- `CFileException::lockViolation`12: se produjo un intento de bloquear una región que ya estaba bloqueada.  
  
- `CFileException::diskFull`14: el disco está lleno.  
  
- `CFileException::endOfFile`15: se alcanzó el final del archivo.  
  
    > [!NOTE]
    >  Estos enumeradores de causa de `CFileException` son distintos de los enumeradores de causa de `CArchiveException`.  
  
    > [!NOTE]
    > `CArchiveException::generic` está desusada. Utilice `genericException` en su lugar. Si `generic` se usa en una aplicación y se crea con /clr, los errores de sintaxis resultantes no serán fáciles de descifrar.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCFiles Nº&30;](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_3.cpp)]  
  
##  <a name="m_loserror"></a>CFileException::m_lOsError  
 Contiene el código de error del sistema operativo para esta excepción.  
  
```  
LONG m_lOsError;  
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte el manual técnico del sistema operativo para obtener una lista de códigos de error. Este miembro de datos es una variable pública de tipo **largo**.  
  
##  <a name="m_strfilename"></a>CFileException::m_strFileName  
 Contiene el nombre del archivo para esta condición de excepción.  
  
```  
CString m_strFileName;  
```  
  
##  <a name="oserrortoexception"></a>CFileException::OsErrorToException  
 Devuelve un enumerador que corresponde a un determinado `lOsError` valor. Si el código de error es desconocido, la función devuelve **CFileException::generic**.  
  
```  
static int PASCAL OsErrorToException(LONG lOsError);
```  
  
### <a name="parameters"></a>Parámetros  
 `lOsError`  
 Código de error específicos del sistema operativo.  
  
### <a name="return-value"></a>Valor devuelto  
 Valor enumerado que corresponde a un valor de error de sistema operativo determinado.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCFiles Nº&27;](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_4.cpp)]  
  
##  <a name="throwerrno"></a>CFileException::ThrowErrno  
 Construye un `CFileException` objeto correspondiente a un determinado `nErrno` valor, a continuación, inicia la excepción.  
  
```  
static void PASCAL ThrowErrno(int nErrno, LPCTSTR lpszFileName = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `nErrno`  
 Código de error entero como se define en el archivo de inclusión de tiempo de ejecución ERRNO. H.  
  
 `lpszFileName`  
 Un puntero a la cadena que contiene el nombre del archivo que provocó la excepción, si está disponible.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCFiles&#28;](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_5.cpp)]  
  
##  <a name="throwoserror"></a>CFileException::ThrowOsError  
 Se produce un `CFileException` correspondiente a una determinada `lOsError` valor. Si el código de error es desconocido, la función produce una excepción que se codifica como **CFileException::generic**.  
  
```  
static void PASCAL ThrowOsError(LONG lOsError, LPCTSTR lpszFileName = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `lOsError`  
 Código de error específicos del sistema operativo.  
  
 `lpszFileName`  
 Un puntero a la cadena que contiene el nombre del archivo que provocó la excepción, si está disponible.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCFiles&#29;](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_6.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [CException (clase)](../../mfc/reference/cexception-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Procesamiento de excepciones](../../mfc/reference/exception-processing.md)




