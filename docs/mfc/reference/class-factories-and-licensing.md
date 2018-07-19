---
title: Generadores de clases y licencias | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros.classes
dev_langs:
- C++
helpviewer_keywords:
- class factories [MFC], and licensing
ms.assetid: 53c4856a-4062-46db-9f69-dd4339f746b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e8f411aeb88a2d76265c6e8c277b367cb1ebce57
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/27/2018
ms.locfileid: "37038242"
---
# <a name="class-factories-and-licensing"></a>Generadores de clases y licencias
Para crear una instancia del control OLE, una aplicación de contenedor llama a una función miembro de fábrica de clase del control. Dado que el control es un objeto OLE real, el generador de clases es responsable de crear instancias del control. Cada clase de control OLE debe tener un generador de clases.  
  
 Otra característica importante de los controles OLE es su capacidad de aplicar una licencia. ControlWizard permite incorporar la licencia durante la creación del proyecto de control. Para obtener más información acerca de las licencias de control, vea el artículo [controles ActiveX: licencias de un ActiveX Control](../../mfc/mfc-activex-controls-licensing-an-activex-control.md).  
  
 En la tabla siguiente se enumera varias macros y funciones que se usan para declarar e implementar el generador de clases del control y a la licencia del control.  
  
### <a name="class-factories-and-licensing"></a>Generadores de clases y licencias  
  
|||  
|-|-|  
|[DECLARE_OLECREATE_EX](#declare_olecreate_ex)|Declara el generador de clases de una página de control o una propiedad OLE.|  
|[IMPLEMENT_OLECREATE_EX](#implement_olecreate_ex)|Implementa el control `GetClassID` función y declara una instancia de la fábrica de clase.|  
|[BEGIN_OLEFACTORY](#begin_olefactory)|Comienza la declaración de las funciones de licencias.|  
|[END_OLEFACTORY](#end_olefactory)|Finaliza la declaración de las funciones de licencias.|  
|[AfxVerifyLicFile](#afxverifylicfile)|Comprueba si un control tiene licencia para su uso en un equipo determinado.|  
  
##  <a name="declare_olecreate_ex"></a>  DECLARE_OLECREATE_EX  
 Declara un generador de clases y la `GetClassID` función miembro de la clase del control.  
  
```   
DECLARE_OLECREATE_EX(class_name)   
```  
  
### <a name="parameters"></a>Parámetros  
 *CLASS_NAME*  
 El nombre de la clase de control.  
  
### <a name="remarks"></a>Comentarios  
 Use esta macro en el archivo de encabezado de la clase de control para un control que no admiten las licencias.  
  
 Tenga en cuenta que esta macro tiene la misma finalidad que el ejemplo de código siguiente:  
  
 [!code-cpp[NVC_MFCAxCtl#14](../../mfc/reference/codesnippet/cpp/class-factories-and-licensing_1.h)]  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxctl.h  
  
##  <a name="implement_olecreate_ex"></a>  IMPLEMENT_OLECREATE_EX  
 Implementa el generador de clases del control y la [GetClassID](../../mfc/reference/colecontrol-class.md#getclassid) función miembro de la clase del control.  
  
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
 *CLASS_NAME*  
 El nombre de la clase de página de propiedades de control.  
  
 *external_name*  
 El nombre de objeto expuesto a las aplicaciones.  
  
 *l, w1, w2, b1, b2, b3, b4, b5, b6, b7, b8*  
 Componentes de la clase **CLSID**. Para obtener más información acerca de estos parámetros, vea la sección Comentarios para [IMPLEMENT_OLECREATE](run-time-object-model-services.md#implement_olecreate).  
  
### <a name="remarks"></a>Comentarios  
 Esta macro debe aparecer en el archivo de implementación para cualquier clase de control que utiliza la `DECLARE_OLECREATE_EX` macro o la `BEGIN_OLEFACTORY` y `END_OLEFACTORY` macros. External name es el identificador del control OLE que se expone a otras aplicaciones. Contenedores utilizan este nombre para solicitar un objeto de esta clase de control.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxctl.h  
  
##  <a name="begin_olefactory"></a>  BEGIN_OLEFACTORY  
 Comienza la declaración de la fábrica de clase en el archivo de encabezado de la clase del control.  
  
``` 
BEGIN_OLEFACTORY(class_name)  
```  
  
### <a name="parameters"></a>Parámetros  
 *CLASS_NAME*  
 Especifica el nombre de la clase de control cuyo es el generador de clases.  
  
### <a name="remarks"></a>Comentarios  
 Las declaraciones de funciones de administrador de licencias de generador de clases deben comenzar inmediatamente después de `BEGIN_OLEFACTORY`.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxctl.h  
  
##  <a name="end_olefactory"></a>  END_OLEFACTORY  
 Finaliza la declaración de generador de clases del control.  
  
```  
END_OLEFACTORY(class_name)   
```  
  
### <a name="parameters"></a>Parámetros  
 *CLASS_NAME*  
 El nombre de la clase de control cuyo es el generador de clases.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxctl.h  
  
##  <a name="afxverifylicfile"></a>  AfxVerifyLicFile  
 Llame a esta función para comprobar que el archivo de licencia con el nombre por `pszLicFileName` es válido para el control OLE.  
  
```   
BOOL AFXAPI AfxVerifyLicFile(
    HINSTANCE  hInstance,  
    LPCTSTR  pszLicFileName,  
    LPOLESTR  pszLicFileContents,  
    UINT cch = -1); 
```  
  
### <a name="parameters"></a>Parámetros  
 *hInstance*  
 El identificador de instancia de la DLL asociada con el control con licencia.  
  
 *pszLicFileName*  
 Apunta a una cadena de caracteres terminada en null que contiene el nombre de archivo de licencia.  
  
 *pszLicFileContents*  
 Señala a una secuencia de bytes que debe coincidir con la secuencia que se encuentra al principio del archivo de licencia.  
  
 *cch*  
 Número de caracteres de *pszLicFileContents*.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el archivo de licencia existe y comienza con la secuencia de caracteres en *pszLicFileContents*; de lo contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Si *cch* es -1, esta función utiliza:  
  
 [!code-cpp[NVC_MFC_Utilities#36](../../mfc/codesnippet/cpp/class-factories-and-licensing_2.cpp)]  

### <a name="requirements"></a>Requisitos  
  **Encabezado** afxctl.h  

## <a name="see-also"></a>Vea también  
 [Macros y funciones globales](../../mfc/reference/mfc-macros-and-globals.md)
