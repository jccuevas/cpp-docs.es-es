---
title: Clase CException
ms.date: 11/04/2016
f1_keywords:
- CException
- AFX/CException
- AFX/CException::CException
- AFX/CException::Delete
- AFX/CException::ReportError
helpviewer_keywords:
- CException [MFC], CException
- CException [MFC], Delete
- CException [MFC], ReportError
ms.assetid: cfacf14d-bfe4-4666-a5c7-38b800512920
ms.openlocfilehash: c3742db7475e626b18e9c073a0b7417a8034863f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373938"
---
# <a name="cexception-class"></a>Clase CException

La clase base para todas las excepciones en la biblioteca MFC (Microsoft Foundation Class).

## <a name="syntax"></a>Sintaxis

```
class AFX_NOVTABLE CException : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CException::CException](#cexception)|Construye un objeto `CException`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CException::Delete](#delete)|Elimina un `CException` objeto.|
|[CException::ReportError](#reporterror)|Notifica un mensaje de error en un cuadro de mensaje al usuario.|

## <a name="remarks"></a>Observaciones

Dado `CException` que es una clase `CException` base abstracta, no se pueden crear objetos directamente; debe crear objetos de clases derivadas. Si necesita crear su `CException`propia clase -style, utilice una de las clases derivadas enumeradas anteriormente como modelo. Asegúrese de que la `IMPLEMENT_DYNAMIC`clase derivada también utiliza .

Las clases derivadas y sus descripciones se enumeran a continuación:

|||
|-|-|
|[CSimpleException](../../mfc/reference/csimpleexception-class.md)|Una clase base para excepciones MFC críticas para recursos|
|[CInvalidArgException](../../mfc/reference/cinvalidargexception-class.md)|Condición de excepción de argumento no válida|
|[CMemoryException](../../mfc/reference/cmemoryexception-class.md)|Excepción de memoria insuficiente|
|[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)|Solicitud de una operación no admitida|
|[CArchiveException](../../mfc/reference/carchiveexception-class.md)|Excepción específica del archivo|
|[CFileException](../../mfc/reference/cfileexception-class.md)|Excepción específica del archivo|
|[CResourceException](../../mfc/reference/cresourceexception-class.md)|Recurso de Windows no encontrado o no creable|
|[COleException](../../mfc/reference/coleexception-class.md)|Excepción OLE|
|[CDBException](../../mfc/reference/cdbexception-class.md)|Excepción de base de datos (es decir, condiciones de excepción que surgen para las clases de base de datos MFC basadas en open database Connectivity)|
|[COleDispatchException](../../mfc/reference/coledispatchexception-class.md)|Excepción de envío OLE (automatización)|
|[CUserException](../../mfc/reference/cuserexception-class.md)|Excepción que indica que no se pudo encontrar un recurso|
|[CDaoException](../../mfc/reference/cdaoexception-class.md)|Excepción de objeto de acceso a datos (es decir, condiciones de excepción que surgen para las clases DAO)|
|[Clase CInternetException](../../mfc/reference/cinternetexception-class.md)|Excepción de Internet (es decir, condiciones de excepción que surjan para las clases de Internet).|

Estas excepciones están diseñadas para usarse con las macros [THROW](exception-processing.md#throw), [THROW_LAST](exception-processing.md#throw_last), [try](exception-processing.md#try), [catch](exception-processing.md#catch), [and_catch](exception-processing.md#and_catch)y [end_catch.](exception-processing.md#end_catch) Para obtener más información sobre las excepciones, vea Procesamiento de [excepciones](exception-processing.md)o vea el artículo Control de [excepciones (MFC)](../exception-handling-in-mfc.md).

Para detectar una excepción específica, utilice la clase derivada adecuada. Para detectar todos los tipos `CException`de excepciones, use y, a `CException`continuación, use [CObject::IsKindOf](cobject-class.md#iskindof) para diferenciar entre clases derivadas. Tenga `CObject::IsKindOf` en cuenta que solo funciona para las clases declaradas con la macro [IMPLEMENT_DYNAMIC,](run-time-object-model-services.md#implement_dynamic) con el fin de aprovechar la comprobación de tipos dinámicos. Cualquier `CException`clase derivada que cree también `IMPLEMENT_DYNAMIC` debe usar la macro.

Puede notificar detalles sobre excepciones al usuario llamando a [GetErrorMessage](cfileexception-class.md#geterrormessage) o [ReportError](#reporterror), dos funciones miembro que funcionan con cualquiera de las clases derivadas de `CException`'s.

Si una de las macros detecta `CException` una excepción, el objeto se elimina automáticamente; no lo elimine usted mismo. Si se detecta una excepción mediante una palabra clave **catch,** no se elimina automáticamente. Consulte el artículo Control de [excepciones (MFC)](../exception-handling-in-mfc.md) para obtener más información sobre cuándo eliminar un objeto de exepción.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](cobject-class.md)

`CException`

## <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

## <a name="cexceptioncexception"></a><a name="cexception"></a>CException::CException

Esta función miembro `CException` construye un objeto.

```
explicit CException(BOOL bAutoDelete);
```

### <a name="parameters"></a>Parámetros

*b_AutoDelete*<br/>
Especifique TRUE si la `CException` memoria del objeto se ha asignado en el montón. Esto hará `CException` que el objeto `Delete` se elimine cuando se llama a la función miembro para eliminar la excepción. Especifique FALSE `CException` si el objeto está en la pila o es un objeto global. En este caso, el `CException` objeto no `Delete` se eliminará cuando se llama a la función miembro.

### <a name="remarks"></a>Observaciones

Normalmente nunca tendría que llamar a este constructor directamente. Una función que produce una excepción `CException`debe crear una instancia de una clase derivada y llamar a su constructor, o debe usar una de las funciones de inicio de MFC, como [AfxThrowFileException](exception-processing.md#afxthrowfileexception), para producir un tipo predefinido. Esta documentación se proporciona solo para su integridad.

## <a name="cexceptiondelete"></a><a name="delete"></a>CException::Delete

Esta función comprueba si `CException` el objeto se creó en el montón y, si es así, llama al operador **delete** en el objeto.

```
void Delete();
```

### <a name="remarks"></a>Observaciones

Al eliminar un `CException` objeto, `Delete` utilice la función miembro para eliminar la excepción. No utilice el operador **delete** `CException` directamente, ya que el objeto puede ser un objeto global o se ha creado en la pila.

Puede especificar si el objeto debe eliminarse cuando se construye el objeto. Para obtener más información, vea [CException::CException](#cexception).

Solo tiene que `Delete` llamar si está utilizando el mecanismo de**captura** de **prueba**- C+++ . Si utiliza las macros MFC **TRY** y **CATCH**, estas macros llamarán automáticamente a esta función.

### <a name="example"></a>Ejemplo

```cpp
CFile* pFile = NULL;
// Constructing a CFile object with this override may throw
// a CFile exception, and won't throw any other exceptions.
// Calling CString::Format() may throw a CMemoryException,
// so we have a catch block for such exceptions, too. Any
// other exception types this function throws will be
// routed to the calling function.
// Note that this example performs the same actions as the
// example for CATCH, but uses C++ try/catch syntax instead
// of using the MFC TRY/CATCH macros. This sample must use
// CException::Delete() to delete the exception objects
// before closing the catch block, while the CATCH example
// implicitly performs the deletion via the macros.
try
{
   pFile = new CFile(_T("C:\\WINDOWS\\SYSTEM.INI"),
      CFile::modeRead | CFile::shareDenyNone);
   ULONGLONG ullLength = pFile->GetLength();
   CString str;
   str.Format(_T("Your SYSTEM.INI file is %u bytes long."), ullLength);
   AfxMessageBox(str);
}
catch(CFileException* pEx)
{
   // Simply show an error message to the user.
   pEx->ReportError();
   pEx->Delete();
}
catch(CMemoryException* pEx)
{
   // We can't recover from this memory exception, so we'll
   // just terminate the app without any cleanup. Normally, an
   // an application should do everything it possibly can to
   // clean up properly and _not_ call AfxAbort().
   pEx->Delete();
   AfxAbort();
}
// If an exception occurrs in the CFile constructor,
// the language will free the memory allocated by new
// and will not complete the assignment to pFile.
// Thus, our clean-up code needs to test for NULL.
if (pFile != NULL)
{
   pFile->Close();
   delete pFile;
}
```

## <a name="cexceptionreporterror"></a><a name="reporterror"></a>CException::ReportError

Llame a esta función miembro para notificar texto de error en un cuadro de mensaje al usuario.

```
virtual int ReportError(
    UINT nType = MB_OK,
    UINT nMessageID = 0);
```

### <a name="parameters"></a>Parámetros

*nType*<br/>
Especifica el estilo del cuadro de mensaje. Aplique cualquier combinación de los [estilos de cuadro de mensaje](styles-used-by-mfc.md#message-box-styles) al cuadro. Si no especifica este parámetro, el valor predeterminado es MB_OK.

*nMessageID*<br/>
Especifica el identificador de recurso (entrada de tabla de cadena) de un mensaje que se mostrará si el objeto de excepción no tiene un mensaje de error. Si es 0, aparece el mensaje "No hay ningún mensaje de error disponible".

### <a name="return-value"></a>Valor devuelto

Un `AfxMessageBox` valor; de lo contrario 0 si no hay suficiente memoria para mostrar el cuadro de mensaje. Consulte [AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox) para obtener los posibles valores devueltos.

### <a name="example"></a>Ejemplo

Este es un ejemplo `CException::ReportError`del uso de . Para ver otro ejemplo, consulte el ejemplo de [CATCH](exception-processing.md#catch).

```cpp
CFile fileInput;
CFileException ex;

// try to open a file for reading.
// The file will certainly not
// exist because there are too many explicit
// directories in the name.

// if the call to Open() fails, ex will be
// initialized with exception
// information.  the call to ex.ReportError() will
// display an appropriate
// error message to the user, such as
// "\Too\Many\Bad\Dirs.DAT contains an
// invalid path."  The error message text will be
// appropriate for the
// file name and error condition.

if (!fileInput.Open(_T("\\Too\\Many\\Bad\\Dirs.DAT"), CFile::modeRead, &ex))
{
  ex.ReportError();
}
else
{
  // the file was opened, so do whatever work
  // with fileInput we were planning...

  fileInput.Close();
}
```

## <a name="see-also"></a>Consulte también

[Clase CObject](cobject-class.md)<br/>
[Gráfico de jerarquías](../hierarchy-chart.md)<br/>
[Procesamiento de excepciones](exception-processing.md)<br/>
[Cómo puedo: Crear mis propias clases de excepción personalizadas](https://go.microsoft.com/fwlink/p/?linkid=128045)
