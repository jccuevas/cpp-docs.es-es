---
title: Generadores de clases y licencias
ms.date: 11/04/2016
helpviewer_keywords:
- class factories [MFC], and licensing
ms.assetid: 53c4856a-4062-46db-9f69-dd4339f746b3
ms.openlocfilehash: e3fed6520cdbe0fd964e4e80e7c9ed9b78296d16
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372306"
---
# <a name="class-factories-and-licensing"></a>Generadores de clases y licencias

Para crear una instancia del control OLE, una aplicación contenedora llama a una función miembro del generador de clases del control. Dado que el control es un objeto OLE real, el generador de clases es responsable de crear instancias del control. Cada clase de control OLE debe tener un generador de clases.

Otra característica importante de los controles OLE es su capacidad para aplicar una licencia. ControlWizard le permite incorporar licencias durante la creación de su proyecto de control. Para obtener más información sobre las licencias de control, consulte el artículo [Controles ActiveX: Licenciar un control ActiveX](../../mfc/mfc-activex-controls-licensing-an-activex-control.md).

En la tabla siguiente se enumeran varias macros y funciones que se usan para declarar e implementar el generador de clases del control y para licenciar el control.

### <a name="class-factories-and-licensing"></a>Generadores de clases y licencias

|||
|-|-|
|[DECLARE_OLECREATE_EX](#declare_olecreate_ex)|Declara el generador de clases para un control OLE o página de propiedades.|
|[IMPLEMENT_OLECREATE_EX](#implement_olecreate_ex)|Implementa la función `GetClassID` del control y declara una instancia del generador de clases.|
|[BEGIN_OLEFACTORY](#begin_olefactory)|Comienza la declaración de cualquier función de licencia.|
|[END_OLEFACTORY](#end_olefactory)|Finaliza la declaración de cualquier función de licencia.|
|[AfxVerifyLicFile](#afxverifylicfile)|Comprueba si un control tiene licencia para su uso en un equipo determinado.|

## <a name="declare_olecreate_ex"></a><a name="declare_olecreate_ex"></a>DECLARE_OLECREATE_EX

Declara un generador de `GetClassID` clases y la función miembro de la clase de control.

```
DECLARE_OLECREATE_EX(class_name)
```

### <a name="parameters"></a>Parámetros

*class_name*<br/>
El nombre de la clase de control.

### <a name="remarks"></a>Observaciones

Utilice esta macro en el archivo de encabezado de clase de control para un control que no admite licencias.

Tenga en cuenta que esta macro tiene el mismo propósito que el ejemplo de código siguiente:

[!code-cpp[NVC_MFCAxCtl#14](../../mfc/reference/codesnippet/cpp/class-factories-and-licensing_1.h)]

### <a name="requirements"></a>Requisitos

  **Encabezado** afxctl.h

## <a name="implement_olecreate_ex"></a><a name="implement_olecreate_ex"></a>IMPLEMENT_OLECREATE_EX

Implementa el generador de clases del control y la función miembro [GetClassID](../../mfc/reference/colecontrol-class.md#getclassid) de la clase de control.

```
IMPLEMENT_OLECREATE_EX(
   class_name,
    external_name,
    l,
    w1,
    w2,
    b1,
    b2,
    b3,
    b4,
    b5,
    b6,
    b7,
    b8)
```

### <a name="parameters"></a>Parámetros

*class_name*<br/>
El nombre de la clase de página de propiedades de control.

*external_name*<br/>
El nombre del objeto expuesto a las aplicaciones.

*l, w1, w2, b1, b2, b3, b4, b5, b6, b7, b8*<br/>
Componentes del CLSID de la clase. Para obtener más información sobre estos parámetros, consulte Comentarios para [IMPLEMENT_OLECREATE](run-time-object-model-services.md#implement_olecreate).

### <a name="remarks"></a>Observaciones

Esta macro debe aparecer en el archivo de implementación para cualquier clase de control que utilice la macro DECLARE_OLECREATE_EX o las macros BEGIN_OLEFACTORY y END_OLEFACTORY. El nombre externo es el identificador del control OLE que se expone a otras aplicaciones. Los contenedores usan este nombre para solicitar un objeto de esta clase de control.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxctl.h

## <a name="begin_olefactory"></a><a name="begin_olefactory"></a>BEGIN_OLEFACTORY

Comienza la declaración de su generador de clases en el archivo de encabezado de la clase de control.

```
BEGIN_OLEFACTORY(class_name)
```

### <a name="parameters"></a>Parámetros

*class_name*<br/>
Especifica el nombre de la clase de control cuyo generador de clases es.

### <a name="remarks"></a>Observaciones

Las declaraciones de las funciones de licencias de fábrica de clase deben comenzar inmediatamente después de BEGIN_OLEFACTORY.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxctl.h

## <a name="end_olefactory"></a><a name="end_olefactory"></a>END_OLEFACTORY

Finaliza la declaración de la fábrica de clases del control.

```
END_OLEFACTORY(class_name)
```

### <a name="parameters"></a>Parámetros

*class_name*<br/>
El nombre de la clase de control cuyo generador de clases es.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxctl.h

## <a name="afxverifylicfile"></a><a name="afxverifylicfile"></a>AfxVerifyLicFile

Llame a esta función para `pszLicFileName` comprobar que el archivo de licencia nombrado por es válido para el control OLE.

```
BOOL AFXAPI AfxVerifyLicFile(
    HINSTANCE  hInstance,
    LPCTSTR  pszLicFileName,
    LPOLESTR  pszLicFileContents,
    UINT cch = -1);
```

### <a name="parameters"></a>Parámetros

*hInstance*<br/>
Identificador de instancia del archivo DLL asociado con el control con licencia.

*pszLicFileName*<br/>
Apunta a una cadena de caracteres terminada en null que contiene el nombre de archivo de licencia.

*pszLicFileContents*<br/>
Señala a una secuencia de bytes que debe coincidir con la secuencia encontrada al principio del archivo de licencia.

*Cch*<br/>
Número de caracteres en *pszLicFileContents*.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el archivo de licencia existe y comienza con la secuencia de caracteres en *pszLicFileContents*; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Si *cch* es -1, esta función utiliza:

[!code-cpp[NVC_MFC_Utilities#36](../../mfc/codesnippet/cpp/class-factories-and-licensing_2.cpp)]

### <a name="requirements"></a>Requisitos

  **Encabezado** afxctl.h

## <a name="see-also"></a>Consulte también

[Macros y variables globales](../../mfc/reference/mfc-macros-and-globals.md)
