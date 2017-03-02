---
title: CException (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CException
dev_langs:
- C++
helpviewer_keywords:
- COleDispatchException class, base class
- CException class
- exceptions, classes for
- CInternetException class, base class
- macros, exception handling
- CNotSupportedException class, base class
- CFileException class, base class
- CDBException class, base class
- CArchiveException class, base class
- CUserException class
- CDaoException class, base class
- CMemoryException class, base class
- COleException class, base class
- CResourceException class, base class
ms.assetid: cfacf14d-bfe4-4666-a5c7-38b800512920
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
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 4cbb69ff79a1b201260d83b1bd568b63519a33b5
ms.lasthandoff: 02/24/2017

---
# <a name="cexception-class"></a>CException (clase)
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
|[CException::ReportError](#reporterror)|Envía un mensaje de error en un cuadro de mensaje al usuario.|  
  
## <a name="remarks"></a>Comentarios  
 Porque `CException` es una clase base abstracta, no se puede crear `CException` objetos directamente, debe crear objetos de clases derivadas. Si necesita crear su propio `CException`-clase de estilo, use una de las clases derivadas enumeradas anteriormente como un modelo. Asegúrese de que su clase derivada también utiliza `IMPLEMENT_DYNAMIC`.  
  
 A continuación se enumeran las clases derivadas y sus descripciones:  
  
|||  
|-|-|  
|[CSimpleException](../../mfc/reference/csimpleexception-class.md)|Una clase base para excepciones de MFC recursos críticos|  
|[CInvalidArgException](../../mfc/reference/cinvalidargexception-class.md)|Condición de excepción de argumento no válido|  
|[CMemoryException](../../mfc/reference/cmemoryexception-class.md)|Excepción de memoria insuficiente|  
|[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)|Solicitud de una operación no admitida|  
|[CArchiveException](../../mfc/reference/carchiveexception-class.md)|Excepción de archivo específico|  
|[CFileException](../../mfc/reference/cfileexception-class.md)|Excepción de archivo específicos|  
|[CResourceException](../../mfc/reference/cresourceexception-class.md)|Recursos de Windows no encuentra o no se puede crear|  
|[COleException](../../mfc/reference/coleexception-class.md)|Excepciones OLE|  
|[CDBException](../../mfc/reference/cdbexception-class.md)|Excepción de base de datos (es decir, las condiciones de excepción que se deriven de clases de base de datos MFC basadas en conectividad abierta de base de datos)|  
|[COleDispatchException](../../mfc/reference/coledispatchexception-class.md)|Excepción de envío (automatización) OLE|  
|[CUserException](../../mfc/reference/cuserexception-class.md)|Excepción que indica que no se pudo encontrar un recurso|  
|[CDaoException](../../mfc/reference/cdaoexception-class.md)|Excepción de objeto (es decir, las condiciones de excepción que se deriven de clases DAO) de acceso a datos|  
|[Clase CInternetException](../../mfc/reference/cinternetexception-class.md)|Excepción de Internet (es decir, las condiciones de excepción que se deriven de clases de Internet).|  
  
 Estas excepciones están diseñadas para usarse con el [THROW](exception-processing.md#throw), [THROW_LAST](exception-processing.md#throw_last), [intente](exception-processing.md#try), [catch](exception-processing.md#catch), [and_catch](exception-processing.md#and_catch), y [end_catch](exception-processing.md#end_catch) macros. Para obtener más información sobre excepciones, vea [excepción procesamiento](exception-processing.md), o consulte el artículo [de control de excepciones (MFC)](../exception-handling-in-mfc.md).  
  
 Para detectar una excepción concreta, utilice la clase derivada adecuada. Catch todos los tipos de excepciones, usar `CException`y, a continuación, usar [CObject:: IsKindOf](cobject-class.md#iskindof) para diferenciar entre `CException`-las clases derivadas. Tenga en cuenta que `CObject::IsKindOf` sólo funciona para las clases que se declara con la [IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic) macro para aprovechar la comprobación de tipo dinámico. Cualquier `CException`-clase derivada que cree debe utilizar el `IMPLEMENT_DYNAMIC` macro demasiado.  
  
 Puede notificar los detalles sobre las excepciones al usuario mediante una llamada a [GetErrorMessage](cfileexception-class.md#geterrormessage) o [ReportError](#reporterror), dos funciones miembro que funcionan con cualquiera de `CException`de las clases derivadas.  
  
 Si se detecta una excepción en uno de las macros, los `CException` se elimina automáticamente el objeto; no se elimina manualmente. Si se detecta una excepción utilizando una **catch** (palabra clave), no se elimina automáticamente. Consulte el artículo [de control de excepciones (MFC)](../exception-handling-in-mfc.md) para obtener más información acerca de cuándo se debe eliminar un objeto de excepción.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](cobject-class.md)  
  
 `CException`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h  
  
##  <a name="a-namecexceptiona--cexceptioncexception"></a><a name="cexception"></a>CException::CException  
 Esta función miembro construye un `CException` objeto.  
  
```  
explicit CException(BOOL bAutoDelete);
```  
  
### <a name="parameters"></a>Parámetros  
 *b_AutoDelete*  
 Especifique **TRUE** si la memoria para el `CException` se ha asignado el objeto en el montón. Esto hará que el `CException` objeto que se eliminará cuando el **eliminar** función miembro se llama para eliminar la excepción. Especifique **FALSE** si la `CException` objeto está en la pila o es un objeto global. En este caso, el `CException` objeto no se podrá eliminar cuando el **eliminar** se llama la función miembro.  
  
### <a name="remarks"></a>Comentarios  
 Normalmente no necesitará llamar directamente a este constructor. Una función que produce una excepción debe crear una instancia de un `CException`-clase derivada y llamar a su constructor, o bien debe generar uso de MFC a las funciones, como [AfxThrowFileException](exception-processing.md#afxthrowfileexception), para producir un tipo predefinido. Esta documentación se proporciona sólo para integridad.  
  
##  <a name="a-namedeletea--cexceptiondelete"></a><a name="delete"></a>CException::Delete  
 Esta función comprueba si la **CException** se creó el objeto en el montón, y si es así, llama a la **eliminar** operador en el objeto.  
  
```  
void Delete();
```  
  
### <a name="remarks"></a>Comentarios  
 Al eliminar una **CException** objeto, utilice la **eliminar** función miembro para eliminar la excepción. No utilice la **eliminar** operador directamente, porque la `CException` objeto puede ser un objeto global o se han creado en la pila.  
  
 Puede especificar si se debe eliminar el objeto cuando se construye el objeto. Para obtener más información, consulte [CException::CException](#cexception).  
  
 Sólo debe llamar a **eliminar** si utiliza C++ **intente**- **catch** mecanismo. Si utiliza las macros MFC **intente** y **CATCH**, a continuación, estas macros se llaman automáticamente a esta función.  
  
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
  
##  <a name="a-namereporterrora--cexceptionreporterror"></a><a name="reporterror"></a>CException::ReportError  
 Llame a esta función miembro para el texto de error de informe en un cuadro de mensaje al usuario.  
  
```  
virtual int ReportError(
    UINT nType = MB_OK,  
    UINT nMessageID = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 `nType`  
 Especifica el estilo del cuadro de mensaje. Aplicar cualquier combinación de los [estilos de cuadro de mensaje](message-box-styles.md) al cuadro. Si no especifica este parámetro, el valor predeterminado es **MB_OK**.  
  
 *nMessageID*  
 Especifica el identificador de recurso (entrada de tabla de cadena) de un mensaje para mostrar si el objeto de excepción no tiene un mensaje de error. Si es 0, el mensaje "ningún mensaje de error está disponible" se muestra.  
  
### <a name="return-value"></a>Valor devuelto  
 Un `AfxMessageBox` valor; en caso contrario, 0 si no hay memoria suficiente para mostrar el cuadro de mensaje. Consulte [AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox) para los posibles valores devueltos.  
  
### <a name="example"></a>Ejemplo  
 Este es un ejemplo del uso de `CException::ReportError`. Para obtener otro ejemplo, vea el ejemplo de [CATCH](exception-processing.md#catch).  
  
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

## <a name="see-also"></a>Vea también  
 [CObject (clase)](cobject-class.md)   
 [Gráfico de jerarquía](../hierarchy-chart.md)   
 [Procesamiento de excepciones](exception-processing.md)   
 [Cómo: crear mis propias clases de excepción personalizada](http://go.microsoft.com/fwlink/linkid=128045)



