---
title: Generadores de clases y licencias
ms.date: 11/04/2016
helpviewer_keywords:
- class factories [MFC], and licensing
ms.assetid: 53c4856a-4062-46db-9f69-dd4339f746b3
ms.openlocfilehash: 18d86122e57af056a50a4d94bac89d65a7b71c7d
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79425932"
---
# <a name="class-factories-and-licensing"></a>Generadores de clases y licencias

Para crear una instancia del control OLE, una aplicación contenedora llama a una función miembro del generador de clases del control. Dado que el control es un objeto OLE real, el generador de clases es responsable de crear instancias del control. Todas las clases de controles OLE deben tener un generador de clases.

Otra característica importante de los controles OLE es su capacidad para aplicar una licencia. ControlWizard permite incorporar licencias durante la creación del proyecto de control. Para obtener más información sobre las licencias de control, vea el artículo [controles ActiveX: licencias de un control ActiveX](../../mfc/mfc-activex-controls-licensing-an-activex-control.md).

En la tabla siguiente se enumeran varias macros y funciones que se usan para declarar e implementar el generador de clases del control y para la licencia del control.

### <a name="class-factories-and-licensing"></a>Generadores de clases y licencias

|||
|-|-|
|[DECLARE_OLECREATE_EX](#declare_olecreate_ex)|Declara el generador de clases para un control OLE o una página de propiedades.|
|[IMPLEMENT_OLECREATE_EX](#implement_olecreate_ex)|Implementa la función `GetClassID` del control y declara una instancia del generador de clases.|
|[BEGIN_OLEFACTORY](#begin_olefactory)|Comienza la declaración de las funciones de licencia.|
|[END_OLEFACTORY](#end_olefactory)|Finaliza la declaración de las funciones de licencia.|
|[AfxVerifyLicFile](#afxverifylicfile)|Comprueba si un control tiene licencia para su uso en un equipo determinado.|

##  <a name="declare_olecreate_ex"></a>DECLARE_OLECREATE_EX

Declara un generador de clases y el `GetClassID` función miembro de la clase de control.

```
DECLARE_OLECREATE_EX(class_name)
```

### <a name="parameters"></a>Parámetros

*class_name*<br/>
Nombre de la clase del control.

### <a name="remarks"></a>Observaciones

Use esta macro en el archivo de encabezado de clase del control para un control que no admita licencias.

Tenga en cuenta que esta macro tiene el mismo propósito que el siguiente ejemplo de código:

[!code-cpp[NVC_MFCAxCtl#14](../../mfc/reference/codesnippet/cpp/class-factories-and-licensing_1.h)]

### <a name="requirements"></a>Requisitos

  **Encabezado** afxctl. h

##  <a name="implement_olecreate_ex"></a>IMPLEMENT_OLECREATE_EX

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
Nombre de la clase de página de propiedades del control.

*external_name*<br/>
El nombre de objeto expuesto a las aplicaciones.

*l, W1, W2, B1, B2, B3, B4, B5, B6, B7, B8*<br/>
Componentes del CLSID de la clase. Para obtener más información sobre estos parámetros, vea los comentarios para obtener [IMPLEMENT_OLECREATE](run-time-object-model-services.md#implement_olecreate).

### <a name="remarks"></a>Observaciones

Esta macro debe aparecer en el archivo de implementación para cualquier clase de control que use la macro DECLARE_OLECREATE_EX o las macros BEGIN_OLEFACTORY y END_OLEFACTORY. El nombre externo es el identificador del control OLE que se expone a otras aplicaciones. Los contenedores usan este nombre para solicitar un objeto de esta clase de control.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxctl. h

##  <a name="begin_olefactory"></a>BEGIN_OLEFACTORY

Comienza la declaración del generador de clases en el archivo de encabezado de la clase de control.

```
BEGIN_OLEFACTORY(class_name)
```

### <a name="parameters"></a>Parámetros

*class_name*<br/>
Especifica el nombre de la clase de control cuyo generador de clases es.

### <a name="remarks"></a>Observaciones

Las declaraciones de las funciones de licencia de generador de clases deben comenzar inmediatamente después de BEGIN_OLEFACTORY.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxctl. h

##  <a name="end_olefactory"></a>END_OLEFACTORY

Finaliza la declaración del generador de clases del control.

```
END_OLEFACTORY(class_name)
```

### <a name="parameters"></a>Parámetros

*class_name*<br/>
Nombre de la clase de control cuyo generador de clases es.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxctl. h

##  <a name="afxverifylicfile"></a>AfxVerifyLicFile

Llame a esta función para comprobar que el archivo de licencia denominado por `pszLicFileName` es válido para el control OLE.

```
BOOL AFXAPI AfxVerifyLicFile(
    HINSTANCE  hInstance,
    LPCTSTR  pszLicFileName,
    LPOLESTR  pszLicFileContents,
    UINT cch = -1);
```

### <a name="parameters"></a>Parámetros

*hInstance*<br/>
Identificador de instancia de la DLL asociada al control con licencia.

*pszLicFileName*<br/>
Apunta a una cadena de caracteres terminada en null que contiene el nombre de archivo de la licencia.

*pszLicFileContents*<br/>
Apunta a una secuencia de bytes que debe coincidir con la secuencia que se encuentra al principio del archivo de licencia.

*CCH*<br/>
Número de caracteres de *pszLicFileContents*.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el archivo de licencia existe y comienza con la secuencia de caracteres en *pszLicFileContents*; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

Si *CCH* es-1, esta función utiliza:

[!code-cpp[NVC_MFC_Utilities#36](../../mfc/codesnippet/cpp/class-factories-and-licensing_2.cpp)]

### <a name="requirements"></a>Requisitos

  **Encabezado** afxctl. h

## <a name="see-also"></a>Consulte también

[Macros y variables globales](../../mfc/reference/mfc-macros-and-globals.md)
