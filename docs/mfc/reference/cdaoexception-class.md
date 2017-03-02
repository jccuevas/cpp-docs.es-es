---
title: Clase CDaoException | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDaoException
dev_langs:
- C++
helpviewer_keywords:
- errors [C++], DAO
- CDaoException class
- DAO (Data Access Objects), exceptions
- exceptions, in MFC DAO classes
- Errors collection, DAO
- collections, DAO errors
ms.assetid: b2b01fa9-7ce2-42a1-842e-40f13dc50da4
caps.latest.revision: 24
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: d1cb1c6dbe50d383981af03cc97d1977be12a5f6
ms.lasthandoff: 02/24/2017

---
# <a name="cdaoexception-class"></a>Clase CDaoException
Representa una condición de excepción que surge de las clases de base de datos MFC basadas en los objetos (DAO) de acceso a datos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CDaoException : public CException  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CDaoException::CDaoException](#cdaoexception)|Construye un objeto `CDaoException`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CDaoException::GetErrorCount](#geterrorcount)|Devuelve el número de errores en la colección de errores del motor de base de datos.|  
|[CDaoException:: GetErrorInfo](#geterrorinfo)|Devuelve información acerca de un objeto de error concreto en la colección de errores.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CDaoException::m_nAfxDaoError](#m_nafxdaoerror)|Contiene un código de error extendido de cualquier error en las clases DAO de MFC.|  
|[CDaoException::m_pErrorInfo](#m_perrorinfo)|Un puntero a un [CDaoErrorInfo](../../mfc/reference/cdaoerrorinfo-structure.md) objeto que contiene información sobre un objeto DAO de error.|  
|[CDaoException::m_scode](#m_scode)|El [SCODE](#m_scode) valor asociado con el error.|  
  
## <a name="remarks"></a>Comentarios  
 La clase incluye a miembros de datos públicos que se puede utilizar para determinar la causa de la excepción. `CDaoException`los objetos se construyen y producidos por las funciones miembro de las clases de base de datos DAO.  
  
> [!NOTE]
>  Las clases de base de datos DAO son distintas de las clases de base de datos MFC basadas en Open Database Connectivity (ODBC). Todos los nombres de clase de base de datos DAO tienen el prefijo "CDao". Aún puede acceso a orígenes de datos ODBC con las clases DAO. En general, son más eficaces que las clases MFC basadas en ODBC, las clases MFC basadas en DAO las clases basadas en DAO pueden tener acceso a datos, incluidos los controladores ODBC, mediante su propio motor de base de datos. Las clases de DAO también admiten operaciones de lenguaje de definición de datos (DDL), como agregar tablas a través de las clases, sin tener que llamar a DAO directamente. Para obtener información sobre las excepciones producidas por las clases ODBC, vea [CDBException](../../mfc/reference/cdbexception-class.md).  
  
 Puede tener acceso a los objetos de excepción dentro del ámbito de un [CATCH](../../mfc/reference/exception-processing.md#catch) expresión. También se puede producir `CDaoException` objetos desde su propio código con el [AfxThrowDaoException](../../mfc/reference/exception-processing.md#afxthrowdaoexception) función global.  
  
 En MFC, todos los errores DAO se expresan como excepciones de tipo `CDaoException`. Cuando se detecta una excepción de este tipo, puede usar `CDaoException` funciones de miembro para recuperar información de los objetos de error DAO almacenados en la colección de errores del motor de base de datos. Cuando se produce cada error, uno o más objetos de error se colocan en la colección de errores. (Normalmente la colección contiene sólo un objeto error; si utiliza un origen de datos ODBC, es más probable obtener varios objetos de error). Cuando otra operación DAO genera un error, se borra la colección de errores y el nuevo objeto de error se coloca en la colección de errores. Las operaciones DAO que no generan un error no tienen efecto en la colección de errores.  
  
 Códigos de error DAO, vea el archivo DAOERR. H. Para obtener información relacionada, vea el tema "Errores interceptables de acceso de datos" en la Ayuda de DAO.  
  
 Para obtener más información sobre el control de excepciones en general o sobre `CDaoException` objetos, consulte los artículos [de control de excepciones (MFC)](../../mfc/exception-handling-in-mfc.md) y [excepciones: excepciones de base de datos](../../mfc/exceptions-database-exceptions.md). El segundo artículo contiene código de ejemplo que ilustra el control de excepciones en DAO.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 `CDaoException`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdao.h  
  
##  <a name="a-namecdaoexceptiona--cdaoexceptioncdaoexception"></a><a name="cdaoexception"></a>CDaoException::CDaoException  
 Construye un objeto `CDaoException`.  
  
```  
CDaoException();
```  
  
### <a name="remarks"></a>Comentarios  
 Normalmente, el marco de trabajo crea los objetos de excepción cuando su código produce una excepción. Rara vez necesitará construir un objeto de excepción explícitamente. Si desea iniciar una `CDaoException` desde su propio código, llame a la función global [AfxThrowDaoException](../../mfc/reference/exception-processing.md#afxthrowdaoexception).  
  
 Sin embargo, puede crear explícitamente un objeto de excepción si va a realizar llamadas directas a DAO a través de los punteros de interfaz DAO que encapsulan las clases MFC. En ese caso, tendrá que recuperar información de error de DAO. Supongamos que se produce un error en DAO cuando se llama a un método DAO a través de la interfaz de DAODatabases a la colección de bases de datos del área de trabajo.  
  
##### <a name="to-retrieve-the-dao-error-information"></a>Para recuperar la información de error DAO  
  
1.  Construir un `CDaoException` objeto.  
  
2.  Llame al objeto de excepción [GetErrorCount](#geterrorcount) función miembro para determinar cuántos objetos de error en la colección de errores del motor de base de datos. (Normalmente sólo uno, si se utiliza un origen de datos ODBC.)  
  
3.  Llame al objeto de excepción [GetErrorInfo](#geterrorinfo) función miembro para recuperar un objeto de error específico a la vez, por su índice en la colección a través del objeto de excepción. Considere el objeto de excepción como un proxy para un objeto DAO error.  
  
4.  Examinar actual [CDaoErrorInfo](../../mfc/reference/cdaoerrorinfo-structure.md) estructura `GetErrorInfo` devuelve en el [miembro m_pErrorInfo](#m_perrorinfo) miembro de datos. Sus miembros proporcionan información sobre el error DAO.  
  
5.  En el caso de un origen de datos ODBC, repita los pasos 3 y 4 según sea necesario para los objetos de error más.  
  
6.  Si crea el objeto de excepción en el montón, elimínelo con el **eliminar** operador cuando termine.  
  
 Para obtener más información sobre el control de errores en las clases DAO de MFC, vea el artículo [excepciones: excepciones de base de datos](../../mfc/exceptions-database-exceptions.md).  
  
##  <a name="a-namegeterrorcounta--cdaoexceptiongeterrorcount"></a><a name="geterrorcount"></a>CDaoException::GetErrorCount  
 Llame a esta función miembro para recuperar el número de objetos de error DAO en la colección de errores del motor de base de datos.  
  
```  
short GetErrorCount();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de objetos de error DAO en la colección de errores del motor de base de datos.  
  
### <a name="remarks"></a>Comentarios  
 Esta información es útil para recorrer en iteración la colección de errores para recuperar cada uno de los objetos de error DAO uno o más en la colección. Para recuperar un objeto error por índice o por número de error DAO, llame a la [GetErrorInfo](#geterrorinfo) función miembro.  
  
> [!NOTE]
>  Normalmente, hay sólo un objeto de error en la colección de errores. Si está trabajando con un origen de datos ODBC, sin embargo, podría haber más de uno.  
  
##  <a name="a-namegeterrorinfoa--cdaoexceptiongeterrorinfo"></a><a name="geterrorinfo"></a>CDaoException:: GetErrorInfo  
 Devuelve información acerca de un objeto de error concreto en la colección de errores.  
  
```  
void GetErrorInfo(int nIndex);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 El índice de la información de error en la colección de errores del motor de base de datos, para la búsqueda por índice.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función miembro para obtener los siguientes tipos de información acerca de la excepción:  
  
-   Código de error  
  
-   Origen  
  
-   Descripción  
  
-   Archivo de ayuda  
  
-   Contexto de ayuda  
  
 `GetErrorInfo`almacena la información en el objeto de excepción `m_pErrorInfo` miembro de datos. Para obtener una breve descripción de la información devuelta, consulte [miembro m_pErrorInfo](#m_perrorinfo). Si se detecta una excepción de tipo `CDaoException` producida por MFC, la `m_pErrorInfo` miembro ya se rellena. Si decide llamar a DAO directamente, debe llamar el objeto de excepción `GetErrorInfo` función miembro para rellenar `m_pErrorInfo`. Para obtener una descripción más detallada, consulte el [CDaoErrorInfo](../../mfc/reference/cdaoerrorinfo-structure.md) estructura.  
  
 Para obtener información sobre las excepciones de DAO y código de ejemplo, vea el artículo [excepciones: excepciones de base de datos](../../mfc/exceptions-database-exceptions.md).  
  
##  <a name="a-namemnafxdaoerrora--cdaoexceptionmnafxdaoerror"></a><a name="m_nafxdaoerror"></a>CDaoException::m_nAfxDaoError  
 Contiene un código de error extendido de MFC.  
  
### <a name="remarks"></a>Comentarios  
 Este código se proporciona en casos donde se ha equivocado un componente específico de las clases DAO de MFC.  
  
 Los valores posibles son:  
  
- **NO_AFX_DAO_ERROR** la operación más reciente no se ha producido un error extendido de MFC. Sin embargo, la operación se haya producido otros errores de DAO o de OLE, por lo que debe comprobar [miembro m_pErrorInfo](#m_perrorinfo) y posiblemente [m_scode](#m_scode).  
  
- **AFX_DAO_ERROR_ENGINE_INITIALIZATION** MFC no pudo inicializar el motor de base de datos Microsoft Jet. OLE podría han podido inicializar o podría haber sido imposible crear una instancia del objeto de motor de base de datos DAO. Normalmente, estos problemas sugieren una instalación incorrecta de DAO o de OLE.  
  
- **AFX_DAO_ERROR_DFX_BIND** una dirección se utiliza en una llamada de función de exchange (DFX) de campos de registros DAO no existe o no es válida (la dirección no se usó para enlazar los datos). Podría ha pasado una dirección incorrecta en una llamada DFX o la dirección puede haber quedado válida entre operaciones DFX.  
  
- **AFX_DAO_ERROR_OBJECT_NOT_OPEN** ha intentado abrir un objeto recordset basado en una definición de consulta o un objeto de definición de tabla que no estaba en estado abierto.  
  
##  <a name="a-namemperrorinfoa--cdaoexceptionmperrorinfo"></a><a name="m_perrorinfo"></a>CDaoException::m_pErrorInfo  
 Contiene un puntero a un `CDaoErrorInfo` estructura que proporciona información sobre el objeto de error DAO que la última vez que recuperó mediante una llamada a [GetErrorInfo](#geterrorinfo).  
  
### <a name="remarks"></a>Comentarios  
 Este objeto contiene la siguiente información:  
  
|CDaoErrorInfo miembro|Información|Significado|  
|--------------------------|-----------------|-------------|  
|**m_lErrorCode**|Código de error|El código de error DAO|  
|`m_strSource`|Origen|El nombre del objeto o aplicación que generó originalmente el error|  
|`m_strDescription`|Descripción|Una cadena descriptiva asociada con el error|  
|`m_strHelpFile`|Archivo de ayuda|Una ruta de acceso a un archivo de Ayuda de Windows en el que el usuario puede obtener información acerca del problema|  
|**m_lHelpContext**|Contexto de ayuda|El identificador de contexto para un tema en el archivo de Ayuda de DAO|  
  
 Para obtener más información acerca de la información contenida en el `CDaoErrorInfo` de objeto, vea el [CDaoErrorInfo](../../mfc/reference/cdaoerrorinfo-structure.md) estructura.  
  
##  <a name="a-namemscodea--cdaoexceptionmscode"></a><a name="m_scode"></a>CDaoException::m_scode  
 Contiene un valor de tipo `SCODE` que describe el error.  
  
### <a name="remarks"></a>Comentarios  
 Se trata de un código OLE. Rara vez necesitará utilizar este valor porque, en casi todos casos, está disponible en la otra información de error más específico de MFC o DAO `CDaoException` miembros de datos.  
  
 Para obtener información acerca de `SCODE`, vea el tema [estructura de OLE códigos de Error](http://msdn.microsoft.com/library/windows/desktop/ms690088) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. El `SCODE` tipo de datos se asigna a la `HRESULT` el tipo de datos.  
  
## <a name="see-also"></a>Vea también  
 [CException (clase)](../../mfc/reference/cexception-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [CException (clase)](../../mfc/reference/cexception-class.md)

