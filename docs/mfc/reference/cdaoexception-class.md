---
title: CDaoException (clase)
ms.date: 11/04/2016
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
ms.openlocfilehash: e5f28b8896fc9e7e5c6a656a64b938cd7af39f42
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507060"
---
# <a name="cdaoexception-class"></a>CDaoException (clase)

Representa una condición de excepción que surge de las clases de base de datos MFC basadas en los objetos (DAO) de acceso a datos.

## <a name="syntax"></a>Sintaxis

```
class CDaoException : public CException
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CDaoException::CDaoException](#cdaoexception)|Construye un objeto `CDaoException`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CDaoException::GetErrorCount](#geterrorcount)|Devuelve el número de errores en la colección de errores del motor de base de datos.|
|[CDaoException::GetErrorInfo](#geterrorinfo)|Devuelve información de error sobre un objeto de error determinado en la colección de errores.|

### <a name="public-data-members"></a>Miembros de datos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CDaoException::m_nAfxDaoError](#m_nafxdaoerror)|Contiene un código de error extendido para cualquier error en las clases DAO de MFC.|
|[CDaoException::m_pErrorInfo](#m_perrorinfo)|Un puntero a un objeto [cdaoerrorinfo (](../../mfc/reference/cdaoerrorinfo-structure.md) que contiene información sobre un objeto de error DAO.|
|[CDaoException::m_scode](#m_scode)|Valor [SCODE](#m_scode) asociado al error.|

## <a name="remarks"></a>Comentarios

La clase incluye miembros de datos públicos que puede usar para determinar la causa de la excepción. `CDaoException`los objetos se construyen y se producen mediante funciones miembro de las clases de base de datos DAO.

> [!NOTE]
>  Las clases de base de datos DAO son distintas de las clases de base de datos MFC basadas en Conectividad abierta de bases de datos (ODBC). Todos los nombres de clase de base de datos DAO tienen el prefijo "CDao". Todavía puede obtener acceso a los orígenes de datos ODBC con las clases DAO. En general, las clases MFC basadas en DAO son más capaces que las clases MFC basadas en ODBC. las clases basadas en DAO pueden tener acceso a los datos, incluidos los controladores ODBC, a través de su propio motor de base de datos. Las clases basadas en DAO también admiten operaciones de lenguaje de definición de datos (DDL), como agregar tablas a través de las clases, sin tener que llamar a DAO directamente. Para obtener información sobre las excepciones producidas por las clases ODBC, vea [CDBException](../../mfc/reference/cdbexception-class.md).

Puede tener acceso a los objetos de excepción dentro del ámbito de una expresión [catch](../../mfc/reference/exception-processing.md#catch) . También puede iniciar `CDaoException` objetos desde su propio código con la función global [AfxThrowDaoException](../../mfc/reference/exception-processing.md#afxthrowdaoexception) .

En MFC, todos los errores de DAO se expresan como excepciones `CDaoException`, de tipo. Cuando se detecta una excepción de este tipo, se pueden usar `CDaoException` funciones miembro para recuperar información de cualquier objeto de error de DAO almacenado en la colección de errores del motor de base de datos. Cuando se produce cada error, se colocan uno o varios objetos de error en la colección de errores. (Normalmente, la colección solo contiene un objeto de error; si está utilizando un origen de datos ODBC, es más probable que obtenga varios objetos de error). Cuando otra operación DAO genera un error, la colección de errores se borra y el nuevo objeto de error se coloca en la colección de errores. Las operaciones DAO que no generan un error no tienen ningún efecto en la colección de errores.

Para ver los códigos de error de DAO, vea el archivo DAOERR. C. Para obtener información relacionada, vea el tema "errores de acceso a datos recapturables" en la ayuda de DAO.

Para obtener más información sobre el control de excepciones en general `CDaoException` o sobre los objetos, vea los artículos [control de excepciones (MFC)](../../mfc/exception-handling-in-mfc.md) y [excepciones: Excepciones](../../mfc/exceptions-database-exceptions.md)de base de datos. El segundo artículo contiene código de ejemplo que muestra el control de excepciones en DAO.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CException (](../../mfc/reference/cexception-class.md)

`CDaoException`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdao. h

##  <a name="cdaoexception"></a>CDaoException:: CDaoException

Construye un objeto `CDaoException`.

```
CDaoException();
```

### <a name="remarks"></a>Comentarios

Normalmente, el marco de trabajo crea objetos de excepción cuando su código produce una excepción. Rara vez es necesario construir un objeto de excepción explícitamente. Si desea producir un `CDaoException` a partir de su propio código, llame a la función global [AfxThrowDaoException](../../mfc/reference/exception-processing.md#afxthrowdaoexception).

Sin embargo, es posible que desee crear explícitamente un objeto de excepción si va a realizar llamadas directas a DAO a través de los punteros de interfaz de DAO que encapsulan las clases MFC. En ese caso, es posible que necesite recuperar la información de error de DAO. Supongamos que se produce un error en DAO al llamar a un método DAO a través de la interfaz DAODatabases en la colección de bases de datos de un área de trabajo.

##### <a name="to-retrieve-the-dao-error-information"></a>Para recuperar la información de error de DAO

1. Construya un `CDaoException` objeto.

1. Llame a la función miembro [GetErrorCount](#geterrorcount) del objeto de la excepción para determinar el número de objetos de error que hay en la colección de errores del motor de base de datos. (Normalmente solo uno, a menos que esté utilizando un origen de datos ODBC).

1. Llame a la función miembro [GetErrorInfo](#geterrorinfo) del objeto de la excepción para recuperar un objeto de error específico cada vez, por índice en la colección, a través del objeto de excepción. Piense en el objeto de excepción como un proxy para un objeto de error DAO.

1. Examine la estructura [cdaoerrorinfo (](../../mfc/reference/cdaoerrorinfo-structure.md) actual que `GetErrorInfo` devuelve en el miembro de datos [m_pErrorInfo](#m_perrorinfo) . Sus miembros proporcionan información sobre el error de DAO.

1. En el caso de un origen de datos ODBC, repita los pasos 3 y 4 según sea necesario, para obtener más objetos de error.

1. Si construyó el objeto de excepción en el montón, elimínelo con el operador **Delete** cuando termine.

Para obtener más información sobre cómo controlar los errores en las clases DAO de MFC [, vea el artículo excepciones: Excepciones](../../mfc/exceptions-database-exceptions.md)de base de datos.

##  <a name="geterrorcount"></a>  CDaoException::GetErrorCount

Llame a esta función miembro para recuperar el número de objetos de error DAO en la colección de errores del motor de base de datos.

```
short GetErrorCount();
```

### <a name="return-value"></a>Valor devuelto

El número de objetos de error de DAO en la colección de errores del motor de base de datos.

### <a name="remarks"></a>Comentarios

Esta información es útil para recorrer en bucle la colección de errores para recuperar cada uno de los objetos de error de DAO de la colección. Para recuperar un objeto de error por índice o por el número de error de DAO, llame a la función miembro [GetErrorInfo](#geterrorinfo) .

> [!NOTE]
>  Normalmente solo hay un objeto de error en la colección de errores. Sin embargo, si trabaja con un origen de datos ODBC, puede haber más de uno.

##  <a name="geterrorinfo"></a>  CDaoException::GetErrorInfo

Devuelve información de error sobre un objeto de error determinado en la colección de errores.

```
void GetErrorInfo(int nIndex);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Índice de la información de error en la colección de errores del motor de base de datos, para la búsqueda por índice.

### <a name="remarks"></a>Comentarios

Llame a esta función miembro para obtener los siguientes tipos de información sobre la excepción:

- Código de error

- source

- DESCRIPCIÓN

- Archivo de ayuda

- Contexto de ayuda

`GetErrorInfo`almacena la información en el miembro de datos `m_pErrorInfo` del objeto de excepción. Para obtener una breve descripción de la información devuelta, vea [m_pErrorInfo](#m_perrorinfo). Si detecta una excepción de tipo `CDaoException` producida por MFC, el `m_pErrorInfo` miembro ya estará rellenado. Si decide llamar directamente a DAO, debe llamar a la función miembro del objeto `GetErrorInfo` de la excepción para rellenarla. `m_pErrorInfo` Para obtener una descripción más detallada, consulte la estructura [cdaoerrorinfo (](../../mfc/reference/cdaoerrorinfo-structure.md) .

Para obtener información sobre las excepciones de DAO y el código de ejemplo [, vea el artículo excepciones: Excepciones](../../mfc/exceptions-database-exceptions.md)de base de datos.

##  <a name="m_nafxdaoerror"></a>  CDaoException::m_nAfxDaoError

Contiene un código de error extendido de MFC.

### <a name="remarks"></a>Comentarios

Este código se proporciona en los casos en los que un componente específico de las clases DAO de MFC ha sido erróneo.

Los valores posibles son:

- NO_AFX_DAO_ERROR la operación más reciente no ha dado como resultado un error extendido de MFC. Sin embargo, la operación podría haber generado otros errores desde DAO u OLE, por lo que debe comprobar [m_pErrorInfo](#m_perrorinfo) y posiblemente [m_scode](#m_scode).

- AFX_DAO_ERROR_ENGINE_INITIALIZATION MFC no pudo inicializar el motor de base de datos de Microsoft Jet. Es posible que no se haya podido inicializar OLE o que no se haya podido crear una instancia del objeto del motor de base de datos DAO. Normalmente, estos problemas sugieren una instalación incorrecta de DAO u OLE.

- AFX_DAO_ERROR_DFX_BIND una dirección usada en una llamada de función de intercambio de campos de registros (DFX) de DAO no existe o no es válida (la dirección no se usó para enlazar datos). Es posible que haya pasado una dirección incorrecta en una llamada DFX o que la dirección haya dejado de ser válida entre las operaciones DFX.

- AFX_DAO_ERROR_OBJECT_NOT_OPEN intentó abrir un conjunto de registros basado en una definición de usuario o un objeto TableDef que no estaba en un estado abierto.

##  <a name="m_perrorinfo"></a>  CDaoException::m_pErrorInfo

Contiene un puntero a una `CDaoErrorInfo` estructura que proporciona información sobre el objeto de error de DAO que recuperó por última vez mediante una llamada a [GetErrorInfo](#geterrorinfo).

### <a name="remarks"></a>Comentarios

Este objeto contiene la siguiente información:

|Miembro Cdaoerrorinfo (|Información|Significado|
|--------------------------|-----------------|-------------|
|`m_lErrorCode`|Código de error|El código de error de DAO|
|`m_strSource`|source|Nombre del objeto o de la aplicación que generó originalmente el error.|
|`m_strDescription`|DESCRIPCIÓN|Cadena descriptiva asociada al error.|
|`m_strHelpFile`|Archivo de ayuda|Una ruta de acceso a un archivo de ayuda de Windows en el que el usuario puede obtener información acerca del problema|
|`m_lHelpContext`|Contexto de ayuda|El ID. de contexto para un tema en el archivo de ayuda de DAO|

Para obtener información completa sobre la información contenida `CDaoErrorInfo` en el objeto, consulte la estructura [cdaoerrorinfo (](../../mfc/reference/cdaoerrorinfo-structure.md) .

##  <a name="m_scode"></a>  CDaoException::m_scode

Contiene un valor de tipo `SCODE` que describe el error.

### <a name="remarks"></a>Comentarios

Se trata de un código OLE. Rara vez tendrá que usar este valor porque, en casi todos los casos, la información de error de MFC o DAO más específica está disponible `CDaoException` en los demás miembros de datos.

Para obtener información acerca de SCODE, consulte la [estructura de temas de códigos de error OLE](/windows/win32/com/structure-of-com-error-codes) en el Windows SDK. El tipo de datos SCODE se asigna al tipo de datos HRESULT.

## <a name="see-also"></a>Vea también

[CException (clase)](../../mfc/reference/cexception-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CException (clase)](../../mfc/reference/cexception-class.md)
