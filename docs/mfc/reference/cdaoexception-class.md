---
title: CDaoException (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDaoException
- AFXDAO/CDaoException
- AFXDAO/CDaoException::CDaoException
- AFXDAO/CDaoException::GetErrorCount
- AFXDAO/CDaoException::GetErrorInfo
- AFXDAO/CDaoException::m_nAfxDaoError
- AFXDAO/CDaoException::m_pErrorInfo
- AFXDAO/CDaoException::m_scode
dev_langs:
- C++
helpviewer_keywords:
- CDaoException [MFC], CDaoException
- CDaoException [MFC], GetErrorCount
- CDaoException [MFC], GetErrorInfo
- CDaoException [MFC], m_nAfxDaoError
- CDaoException [MFC], m_pErrorInfo
- CDaoException [MFC], m_scode
ms.assetid: b2b01fa9-7ce2-42a1-842e-40f13dc50da4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 38ac86784216fdc81eb73c56f82e8f7b6744941d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46431819"
---
# <a name="cdaoexception-class"></a>CDaoException (clase)

Representa una condición de excepción que surge de las clases de base de datos MFC basadas en los objetos (DAO) de acceso a datos.

## <a name="syntax"></a>Sintaxis

```
class CDaoException : public CException
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CDaoException::CDaoException](#cdaoexception)|Construye un objeto `CDaoException`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CDaoException::GetErrorCount](#geterrorcount)|Devuelve el número de errores en la colección de errores del motor de base de datos.|
|[CDaoException:: GetErrorInfo](#geterrorinfo)|Devuelve información de error sobre un objeto de error concreto en la colección de errores.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[CDaoException::m_nAfxDaoError](#m_nafxdaoerror)|Contiene un código de error extendida para cualquier error en las clases DAO de MFC.|
|[CDaoException::m_pErrorInfo](#m_perrorinfo)|Un puntero a un [CDaoErrorInfo](../../mfc/reference/cdaoerrorinfo-structure.md) objeto que contiene información sobre un objeto de error DAO.|
|[CDaoException::m_scode](#m_scode)|El [SCODE](#m_scode) valor asociado con el error.|

## <a name="remarks"></a>Comentarios

La clase incluye a miembros de datos públicos que puede usar para determinar la causa de la excepción. `CDaoException` los objetos se construye y producidos por las funciones miembro de las clases de base de datos DAO.

> [!NOTE]
>  Las clases de base de datos DAO son distintas de las clases de base de datos MFC basadas en Open Database Connectivity (ODBC). Todos los nombres de clase de base de datos DAO tienen el prefijo "CDao". Todavía puede acceso a orígenes de datos ODBC con las clases DAO. En general, son más eficaces que las clases MFC basadas en ODBC; las clases MFC basadas en DAO las clases basadas en DAO pueden tener acceso a datos, incluidos los controladores ODBC, a través de su propio motor de base de datos. Las clases basadas en DAO también admiten las operaciones de lenguaje de definición de datos (DDL), como agregar tablas a través de las clases, sin tener que llamar a DAO directamente. Para obtener información sobre las excepciones producidas por las clases ODBC, vea [CDBException](../../mfc/reference/cdbexception-class.md).

Puede tener acceso a los objetos de excepción dentro del ámbito de un [CATCH](../../mfc/reference/exception-processing.md#catch) expresión. También se puede producir `CDaoException` objetos desde su propio código con el [AfxThrowDaoException](../../mfc/reference/exception-processing.md#afxthrowdaoexception) función global.

En MFC, todos los errores DAO se expresan como excepciones de tipo `CDaoException`. Cuando se detecta una excepción de este tipo, puede usar `CDaoException` las funciones miembro para recuperar la información de los objetos de error DAO almacenados en la colección de errores del motor de base de datos. Cuando se produce cada error, uno o más objetos de error se colocan en la colección de errores. (Normalmente la colección contiene un solo objeto de error; si usa un origen de datos ODBC, es más probable que obtenga varios objetos de error). Cuando otra operación DAO genera un error, se borra la colección de errores y se coloca el nuevo objeto de error en la colección de errores. Las operaciones de DAO que generan un error no tienen ningún efecto en la colección de errores.

Para los códigos de error DAO, vea el archivo DAOERR. H. Para obtener información relacionada, vea el tema "Errores interceptables de acceso de datos" en la Ayuda de DAO.

Para obtener más información sobre el control de excepciones en general, o sobre `CDaoException` objetos, consulte los artículos [de control de excepciones (MFC)](../../mfc/exception-handling-in-mfc.md) y [excepciones: excepciones de base de datos](../../mfc/exceptions-database-exceptions.md). El segundo artículo contiene código de ejemplo que muestra el control de excepciones en DAO.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CDaoException`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdao.h

##  <a name="cdaoexception"></a>  CDaoException::CDaoException

Construye un objeto `CDaoException`.

```
CDaoException();
```

### <a name="remarks"></a>Comentarios

Normalmente, el marco de trabajo crea los objetos de excepción cuando su código produce una excepción. Rara vez deberá construir explícitamente un objeto de excepción. Si desea producir una `CDaoException` desde su propio código, llame a la función global [AfxThrowDaoException](../../mfc/reference/exception-processing.md#afxthrowdaoexception).

Sin embargo, es posible que desee crear explícitamente un objeto de excepción si se realizan llamadas directas a DAO a través de los punteros de interfaz DAO que encapsulan las clases MFC. En ese caso, es posible que deba recuperar información de error de DAO. Supongamos que se produce un error en DAO cuando se llama a un método DAO a través de la interfaz DAODatabases a la colección de bases de datos de un área de trabajo.

##### <a name="to-retrieve-the-dao-error-information"></a>Para recuperar la información de error DAO

1. Construir un `CDaoException` objeto.

1. Llamar al objeto de excepción [GetErrorCount](#geterrorcount) función miembro para determinar cuántos objetos de error que se encuentran en la colección de errores del motor de base de datos. (Normalmente solo uno, a menos que se usa un origen de datos ODBC.)

1. Llamar al objeto de excepción [GetErrorInfo](#geterrorinfo) función miembro para recuperar un objeto de error específico a la vez, por índice de la colección a través del objeto de excepción. Pensar en el objeto de excepción como un proxy para un objeto de error DAO.

1. Examinar actual [CDaoErrorInfo](../../mfc/reference/cdaoerrorinfo-structure.md) estructura que `GetErrorInfo` devuelve en el [miembro m_pErrorInfo](#m_perrorinfo) miembro de datos. Sus miembros proporcionan información sobre el error DAO.

1. En el caso de un origen de datos ODBC, repita los pasos 3 y 4 según sea necesario, para obtener más objetos de error.

1. Si se construye el objeto de excepción en el montón, eliminarla con el **eliminar** operador cuando termine.

Para obtener más información sobre el control de errores en las clases DAO de MFC, vea el artículo [excepciones: excepciones de base de datos](../../mfc/exceptions-database-exceptions.md).

##  <a name="geterrorcount"></a>  CDaoException::GetErrorCount

Llame a esta función miembro para recuperar el número de objetos de error DAO en la colección de errores del motor de base de datos.

```
short GetErrorCount();
```

### <a name="return-value"></a>Valor devuelto

El número de objetos de error DAO de colección de errores del motor de base de datos.

### <a name="remarks"></a>Comentarios

Esta información es útil para recorrer en iteración la colección de errores para recuperar cada uno de los objetos de error DAO uno o más en la colección. Para recuperar un objeto de error por índice o por número de error DAO, llame el [GetErrorInfo](#geterrorinfo) función miembro.

> [!NOTE]
>  Normalmente, hay un solo objeto de error en la colección de errores. Si está trabajando con un origen de datos ODBC, sin embargo, podría haber más de uno.

##  <a name="geterrorinfo"></a>  CDaoException:: GetErrorInfo

Devuelve información de error sobre un objeto de error concreto en la colección de errores.

```
void GetErrorInfo(int nIndex);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
El índice de la información de error en la colección de errores del motor de base de datos, para la búsqueda por índice.

### <a name="remarks"></a>Comentarios

Llame a esta función miembro para obtener los siguientes tipos de información sobre la excepción:

- Código de error

- Origen

- Descripción

- Archivo de ayuda

- Contexto de ayuda

`GetErrorInfo` almacena la información en el objeto de excepción `m_pErrorInfo` miembro de datos. Para obtener una descripción breve de la información devuelta, consulte [miembro m_pErrorInfo](#m_perrorinfo). Si se detecta una excepción de tipo `CDaoException` producidas por MFC, la `m_pErrorInfo` miembros ya se rellena. Si decide llamar a DAO directamente, debe llamar al objeto de excepción `GetErrorInfo` función miembro para rellenar `m_pErrorInfo`. Para obtener una descripción más detallada, consulte el [CDaoErrorInfo](../../mfc/reference/cdaoerrorinfo-structure.md) estructura.

Para obtener información sobre las excepciones de DAO y el código de ejemplo, consulte el artículo [excepciones: excepciones de base de datos](../../mfc/exceptions-database-exceptions.md).

##  <a name="m_nafxdaoerror"></a>  CDaoException::m_nAfxDaoError

Contiene un código de error extendido de MFC.

### <a name="remarks"></a>Comentarios

Este código se proporciona en los casos donde se ha equivocado un componente específico de las clases DAO de MFC.

Los valores posibles son:

- Error extendido de NO_AFX_DAO_ERROR MFC no se ha producido la operación más reciente. Sin embargo, la operación se han generado otros errores de DAO o de OLE, por lo que debe comprobar [miembro m_pErrorInfo](#m_perrorinfo) y posiblemente [m_scode](#m_scode).

- AFX_DAO_ERROR_ENGINE_INITIALIZATION MFC no se pudo inicializar el motor de base de datos Microsoft Jet. OLE es posible que no han podido inicializar o podría haber sido imposible crear una instancia del objeto de motor de base de datos DAO. Normalmente, estos problemas sugieren una instalación incorrecta de DAO u OLE.

- AFX_DAO_ERROR_DFX_BIND una dirección utilizada en una llamada de función DAO (DFX) de intercambio de campos de registros no existe o no es válido (no ha usado la dirección para enlazar datos). Es posible que ha pasado una dirección incorrecta en una llamada DFX o la dirección puede ser válida entre operaciones DFX.

- AFX_DAO_ERROR_OBJECT_NOT_OPEN intentó abrir un conjunto de registros según una definición de consulta o un objeto de definición de tabla que no estaba en estado abierto.

##  <a name="m_perrorinfo"></a>  CDaoException::m_pErrorInfo

Contiene un puntero a un `CDaoErrorInfo` estructura que proporciona información sobre el objeto de error DAO que la última vez que recuperó mediante una llamada a [GetErrorInfo](#geterrorinfo).

### <a name="remarks"></a>Comentarios

Este objeto contiene la información siguiente:

|CDaoErrorInfo miembro|Información|Significado|
|--------------------------|-----------------|-------------|
|`m_lErrorCode`|Código de error|El código de error DAO|
|`m_strSource`|Origen|El nombre del objeto o la aplicación que generó originalmente el error|
|`m_strDescription`|Descripción|Una cadena descriptiva asociada con el error|
|`m_strHelpFile`|Archivo de ayuda|Una ruta de acceso a un archivo de Ayuda de Windows en el que el usuario puede obtener información acerca del problema|
|`m_lHelpContext`|Contexto de ayuda|Identificador de contexto para un tema en el archivo de Ayuda de DAO|

Para obtener detalles completos acerca de la información contenida en el `CDaoErrorInfo` de objetos, consulte el [CDaoErrorInfo](../../mfc/reference/cdaoerrorinfo-structure.md) estructura.

##  <a name="m_scode"></a>  CDaoException::m_scode

Contiene un valor de tipo `SCODE` que describe el error.

### <a name="remarks"></a>Comentarios

Se trata de un código OLE. Rara vez necesitará utilizar este valor porque, en casi todos los casos, está disponible en la otra información de error más específica de MFC o DAO `CDaoException` los miembros de datos.

Para obtener información acerca de SCODE, vea el tema [estructura de OLE códigos de Error](/windows/desktop/com/structure-of-com-error-codes) en el SDK de Windows. El tipo de datos SCODE se asigna al tipo de datos HRESULT.

## <a name="see-also"></a>Vea también

[CException (clase)](../../mfc/reference/cexception-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CException (clase)](../../mfc/reference/cexception-class.md)
