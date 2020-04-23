---
title: Clase CDaoException
ms.date: 09/17/2019
f1_keywords:
- CDaoException
- AFXDAO/CDaoException
- AFXDAO/CDaoException::CDaoException
- AFXDAO/CDaoException::GetErrorCount
- AFXDAO/CDaoException::GetErrorInfo
- AFXDAO/CDaoException::m_nAfxDaoError
- AFXDAO/CDaoException::m_pErrorInfo
- AFXDAO/CDaoException::m_scode
helpviewer_keywords:
- CDaoException [MFC], CDaoException
- CDaoException [MFC], GetErrorCount
- CDaoException [MFC], GetErrorInfo
- CDaoException [MFC], m_nAfxDaoError
- CDaoException [MFC], m_pErrorInfo
- CDaoException [MFC], m_scode
ms.assetid: b2b01fa9-7ce2-42a1-842e-40f13dc50da4
ms.openlocfilehash: 935d7870d68554d702e2ad762e83343cb518b2b8
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754725"
---
# <a name="cdaoexception-class"></a>Clase CDaoException

Representa una condición de excepción que surge de las clases de base de datos MFC basadas en los objetos (DAO) de acceso a datos. DAO 3.6 es la versión final, y se considera obsoleto.

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
|[CDaoException::GetErrorCount](#geterrorcount)|Devuelve el número de errores de la colección Errors del motor de base de datos.|
|[CDaoException::GetErrorInfo](#geterrorinfo)|Devuelve información de error sobre un objeto de error determinado en el Errors colección.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDaoException::m_nAfxDaoError](#m_nafxdaoerror)|Contiene un código de error extendido para cualquier error en las clases DAO de MFC.|
|[CDaoException::m_pErrorInfo](#m_perrorinfo)|Puntero a un [CDaoErrorInfo](../../mfc/reference/cdaoerrorinfo-structure.md) objeto que contiene información sobre un dao objeto de error.|
|[CDaoException::m_scode](#m_scode)|El valor [SCODE](#m_scode) asociado al error.|

## <a name="remarks"></a>Observaciones

La clase incluye miembros de datos públicos que puede usar para determinar la causa de la excepción. `CDaoException`objetos se construyen y se producen mediante las funciones miembro de las clases de base de datos DAO.

> [!NOTE]
> Las clases de base de datos DAO son distintas de las clases de base de datos MFC basadas en Open Database Connectivity (ODBC). Todos los nombres de clase de base de datos DAO tienen el prefijo "CDao". Todavía puede tener acceso a orígenes de datos ODBC con las clases DAO. En general, las clases MFC basadas en DAO son más capaces que las clases MFC basadas en ODBC; las clases basadas en DAO pueden tener acceso a los datos, incluso a través de controladores ODBC, a través de su propio motor de base de datos. Las clases basadas en DAO también admiten operaciones de lenguaje de definición de datos (DDL), como agregar tablas a través de las clases, sin tener que llamar a DAO directamente. Para obtener información sobre las excepciones producidas por las clases ODBC, vea [CDBException](../../mfc/reference/cdbexception-class.md).

Puede tener acceso a objetos de excepción dentro del ámbito de una expresión [CATCH.](../../mfc/reference/exception-processing.md#catch) También puede `CDaoException` producir objetos desde su propio código con la función global [AfxThrowDaoException.](../../mfc/reference/exception-processing.md#afxthrowdaoexception)

En MFC, todos los errores DAO se `CDaoException`expresan como excepciones, de tipo . Cuando se detecta una excepción de `CDaoException` este tipo, puede usar funciones miembro para recuperar información de cualquier objeto de error DAO almacenado en la colección Errors del motor de base de datos. A medida que se produce cada error, uno o varios objetos de error se colocan en el errores colección. (Normalmente, la colección contiene solo un objeto de error; si está utilizando un origen de datos ODBC, es más probable que obtenga varios objetos de error.) Cuando otra operación DAO genera un error, se borra la colección Errors y el nuevo objeto de error se coloca en la colección Errors. Las operaciones DAO que no generan un error no tienen ningún efecto en la colección Errors.

Para obtener códigos de error DAO, consulte el archivo DAOERR. H. Para obtener información relacionada, consulte el tema "Errores de acceso a datos intercambiables" en la Ayuda de DAO.

Para obtener más información sobre el `CDaoException` control de excepciones en general o sobre objetos, vea los artículos Control de excepciones [(MFC)](../../mfc/exception-handling-in-mfc.md) y [Excepciones: Excepciones](../../mfc/exceptions-database-exceptions.md)de base de datos . El segundo artículo contiene código de ejemplo que ilustra el control de excepciones en DAO.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CDaoException`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdao.h

## <a name="cdaoexceptioncdaoexception"></a><a name="cdaoexception"></a>CDaoException::CDaoException

Construye un objeto `CDaoException`.

```
CDaoException();
```

### <a name="remarks"></a>Observaciones

Normalmente, el marco de trabajo crea objetos de excepción cuando su código produce una excepción. Rara vez es necesario construir un objeto de excepción explícitamente. Si desea iniciar `CDaoException` un desde su propio código, llame a la función global [AfxThrowDaoException](../../mfc/reference/exception-processing.md#afxthrowdaoexception).

Sin embargo, es posible que desee crear explícitamente un objeto de excepción si va a realizar llamadas directas a DAO a través de los punteros de interfaz DAO que encapsulan las clases MFC. En ese caso, es posible que deba recuperar información de error de DAO. Supongamos que se produce un error en DAO cuando se llama a un método DAO a través de la interfaz DAODatabases a la colección Databases de un área de trabajo.

##### <a name="to-retrieve-the-dao-error-information"></a>Para recuperar la información de error de DAO

1. Construir `CDaoException` un objeto.

1. Llame a la función miembro [GetErrorCount](#geterrorcount) del objeto de excepción para determinar cuántos objetos de error hay en la colección Errors del motor de base de datos. (Normalmente solo uno, a menos que utilice un origen de datos ODBC.)

1. Llame a la función miembro [GetErrorInfo](#geterrorinfo) del objeto de excepción para recuperar un objeto de error específico a la vez, por índice de la colección, a través del objeto de excepción. Piense en el objeto de excepción como un proxy para un objeto de error DAO.

1. Examine la actual [CDaoErrorInfo](../../mfc/reference/cdaoerrorinfo-structure.md) estructura que `GetErrorInfo` devuelve en el [m_pErrorInfo](#m_perrorinfo) miembro de datos. Sus miembros proporcionan información sobre el error DAO.

1. En el caso de un origen de datos ODBC, repita los pasos 3 y 4 según sea necesario, para obtener más objetos de error.

1. Si construyó el objeto de excepción en el montón, elimínelo con el operador **delete** cuando termine.

Para obtener más información sobre el control de errores en las clases DAO de MFC, vea el artículo [Excepciones: excepciones](../../mfc/exceptions-database-exceptions.md)de base de datos .

## <a name="cdaoexceptiongeterrorcount"></a><a name="geterrorcount"></a>CDaoException::GetErrorCount

Llame a esta función miembro para recuperar el número de objetos de error DAO en el motor de base de datos Errors colección.

```
short GetErrorCount();
```

### <a name="return-value"></a>Valor devuelto

El número de objetos de error DAO en la colección Errors del motor de base de datos.

### <a name="remarks"></a>Observaciones

Esta información es útil para recorrer en bucle la colección Errors para recuperar cada uno de los objetos de error DAO de la colección. Para recuperar un objeto de error por índice o por número de error DAO, llame a la [GetErrorInfo](#geterrorinfo) función miembro.

> [!NOTE]
> Normalmente, solo hay un objeto de error en la colección Errors. Sin embargo, si está trabajando con un origen de datos ODBC, podría haber más de uno.

## <a name="cdaoexceptiongeterrorinfo"></a><a name="geterrorinfo"></a>CDaoException::GetErrorInfo

Devuelve información de error sobre un objeto de error determinado en el Errors colección.

```cpp
void GetErrorInfo(int nIndex);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
El índice de la información de error de la colección Errors del motor de base de datos, para la búsqueda por índice.

### <a name="remarks"></a>Observaciones

Llame a esta función miembro para obtener los siguientes tipos de información acerca de la excepción:

- Código de error

- Source

- Descripción

- Archivo de ayuda

- Contexto de ayuda

`GetErrorInfo`almacena la información en el `m_pErrorInfo` miembro de datos del objeto de excepción. Para obtener una breve descripción de la información devuelta, consulte [m_pErrorInfo](#m_perrorinfo). Si detecta una excepción de tipo `CDaoException` `m_pErrorInfo` iniciada por MFC, el miembro ya se rellenará. Si decide llamar a DAO directamente, debe `GetErrorInfo` llamar a la `m_pErrorInfo`función miembro del objeto de excepción usted mismo para rellenar . Para obtener una descripción más detallada, vea el [CDaoErrorInfo](../../mfc/reference/cdaoerrorinfo-structure.md) estructura.

Para obtener información acerca de las excepciones DAO y código de ejemplo, vea el artículo [Excepciones: excepciones](../../mfc/exceptions-database-exceptions.md)de base de datos .

## <a name="cdaoexceptionm_nafxdaoerror"></a><a name="m_nafxdaoerror"></a>CDaoException::m_nAfxDaoError

Contiene un código de error extendido mfc.

### <a name="remarks"></a>Observaciones

Este código se proporciona en los casos en que un componente específico de las clases DAO de MFC ha incurrido en error.

Los valores posibles son:

- NO_AFX_DAO_ERROR La operación más reciente no dio lugar a un error extendido de MFC. Sin embargo, la operación podría haber producido otros errores de DAO u OLE, por lo que debe comprobar [m_pErrorInfo](#m_perrorinfo) y posiblemente [m_scode](#m_scode).

- AFX_DAO_ERROR_ENGINE_INITIALIZATION MFC no pudo inicializar el motor de base de datos Microsoft Jet. OLE podría haber fallado al inicializarse, o podría haber sido imposible crear una instancia del objeto de motor de base de datos DAO. Estos problemas suelen sugerir una mala instalación de DAO u OLE.

- AFX_DAO_ERROR_DFX_BIND Una dirección utilizada en una llamada de función de intercambio de campos de registros DAO (DFX) no existe o no es válida (la dirección no se usó para enlazar datos). Es posible que haya pasado una dirección incorrecta en una llamada DFX o que la dirección no sea válida entre las operaciones DFX.

- AFX_DAO_ERROR_OBJECT_NOT_OPEN Ha intentado abrir un conjunto de registros basado en una definición de consulta o un objeto de definición de tabla que no estaba en un estado abierto.

## <a name="cdaoexceptionm_perrorinfo"></a><a name="m_perrorinfo"></a>CDaoException::m_pErrorInfo

Contiene un puntero `CDaoErrorInfo` a una estructura que proporciona información sobre el objeto de error DAO que recuperó por última vez llamando a [GetErrorInfo](#geterrorinfo).

### <a name="remarks"></a>Observaciones

Este objeto contiene la siguiente información:

|Miembro CDaoErrorInfo|Information|Significado|
|--------------------------|-----------------|-------------|
|`m_lErrorCode`|Código de error|El código de error DAO|
|`m_strSource`|Source|El nombre del objeto o aplicación que generó originalmente el error|
|`m_strDescription`|Descripción|Una cadena descriptiva asociada con el error|
|`m_strHelpFile`|Archivo de ayuda|Una ruta de acceso a un archivo de Ayuda de Windows en el que el usuario puede obtener información sobre el problema|
|`m_lHelpContext`|Contexto de ayuda|El identificador de contexto de un tema en el archivo de Ayuda de DAO|

Para obtener información detallada sobre `CDaoErrorInfo` la información contenida en el objeto, vea el [CDaoErrorInfo](../../mfc/reference/cdaoerrorinfo-structure.md) estructura.

## <a name="cdaoexceptionm_scode"></a><a name="m_scode"></a>CDaoException::m_scode

Contiene un valor `SCODE` de tipo que describe el error.

### <a name="remarks"></a>Observaciones

Este es un código OLE. Rara vez tendrá que usar este valor porque, en casi todos los casos, la `CDaoException` información de error MFC o DAO más específica está disponible en los demás miembros de datos.

Para obtener información acerca de SCODE, vea el tema [Estructura de códigos de error OLE](/windows/win32/com/structure-of-com-error-codes) en el Windows SDK. El tipo de datos SCODE se asigna al tipo de datos HRESULT.

## <a name="see-also"></a>Vea también

[Clase CException](../../mfc/reference/cexception-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clase CException](../../mfc/reference/cexception-class.md)
