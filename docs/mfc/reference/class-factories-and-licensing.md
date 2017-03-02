---
title: Generadores de clases y licencias | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.macros.classes
dev_langs:
- C++
helpviewer_keywords:
- class factories, and licensing
ms.assetid: 53c4856a-4062-46db-9f69-dd4339f746b3
caps.latest.revision: 13
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
ms.sourcegitcommit: 17a158366f94d27b7a46917282425d652e6b9042
ms.openlocfilehash: a8ef7ba19d2337e4e50f34d7cdd528024a1d90aa
ms.lasthandoff: 02/24/2017

---
# <a name="class-factories-and-licensing"></a>Generadores de clases y licencias
Para crear una instancia del control OLE, una aplicación de contenedor llama a una función miembro de fábrica de clase del control. Dado que el control es un objeto OLE, el generador de clases es responsable de crear instancias del control. Cada clase de control OLE debe tener un generador de clases.  
  
 Otra característica importante de los controles OLE es su capacidad para aplicar una licencia. ControlWizard permite incorporar licencias durante la creación de su proyecto de control. Para obtener más información acerca de las licencias de control, vea el artículo [controles ActiveX: licencias de un ActiveX Control](../../mfc/mfc-activex-controls-licensing-an-activex-control.md).  
  
 La tabla siguiente enumeran varias macros y funciones que se utilizan para declarar e implementar la fábrica de clase del control y la licencia del control.  
  
### <a name="class-factories-and-licensing"></a>Generadores de clases y licencias  
  
|||  
|-|-|  
|[DECLARE_OLECREATE_EX](#declare_olecreate_ex)|Declara el generador de clases de una página de control o la propiedad OLE.|  
|[IMPLEMENT_OLECREATE_EX](#implement_olecreate_ex)|Implementa el control `GetClassID` función y declara una instancia de la fábrica de clase.|  
|[BEGIN_OLEFACTORY](#begin_olefactory)|Comienza la declaración de las funciones de administración de licencias.|  
|[END_OLEFACTORY](#end_olefactory)|Finaliza la declaración de las funciones de administración de licencias.|  
|[AfxVerifyLicFile](#afxverifylicfile)|Comprueba si un control con licencia para su uso en un equipo determinado.|  
  
##  <a name="a-namedeclareolecreateexa--declareolecreateex"></a><a name="declare_olecreate_ex"></a>DECLARE_OLECREATE_EX  
 Declara un generador de clases y el `GetClassID` función miembro de la clase del control.  
  
```   
DECLARE_OLECREATE_EX(class_name)   
```  
  
### <a name="parameters"></a>Parámetros  
 *CLASS_NAME*  
 El nombre de la clase del control.  
  
### <a name="remarks"></a>Comentarios  
 Use esta macro en el archivo de encabezado de la clase de control para un control que no es compatible con las licencias.  
  
 Tenga en cuenta que esta macro tiene la misma finalidad que el ejemplo de código siguiente:  
  
 [!code-cpp[NVC_MFCAxCtl&#14;](../../mfc/reference/codesnippet/cpp/class-factories-and-licensing_1.h)]  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxctl.h  
  
##  <a name="a-nameimplementolecreateexa--implementolecreateex"></a><a name="implement_olecreate_ex"></a>IMPLEMENT_OLECREATE_EX  
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
  
 *l, w1, w2, b1, b2, b3, b4, b5, b6, b7, M8*  
 Componentes de la clase **CLSID**. Para obtener más información sobre estos parámetros, vea la sección Comentarios para [IMPLEMENT_OLECREATE](run-time-object-model-services.md#implement_olecreate).  
  
### <a name="remarks"></a>Comentarios  
 Esta macro debe aparecer en el archivo de implementación para cualquier clase de control que utiliza la `DECLARE_OLECREATE_EX` macro o `BEGIN_OLEFACTORY` y `END_OLEFACTORY` macros. External name es el identificador del control OLE que se expone a otras aplicaciones. Contenedores utilizan este nombre para solicitar un objeto de esta clase de control.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxctl.h  
  
##  <a name="a-namebeginolefactorya--beginolefactory"></a><a name="begin_olefactory"></a>BEGIN_OLEFACTORY  
 Comienza la declaración de la fábrica de clase en el archivo de encabezado de la clase del control.  
  
``` 
BEGIN_OLEFACTORY(class_name)  
```  
  
### <a name="parameters"></a>Parámetros  
 *CLASS_NAME*  
 Especifica el nombre de la clase control cuyo generador de clases que se trata.  
  
### <a name="remarks"></a>Comentarios  
 Las declaraciones de funciones de administrador de licencias de generador de clases deben comenzar inmediatamente después de `BEGIN_OLEFACTORY`.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxctl.h  
  
##  <a name="a-nameendolefactorya--endolefactory"></a><a name="end_olefactory"></a>END_OLEFACTORY  
 Finaliza la declaración de fábrica de clase del control.  
  
```  
END_OLEFACTORY(class_name)   
```  
  
### <a name="parameters"></a>Parámetros  
 *CLASS_NAME*  
 El nombre de la clase control cuyo generador de clases que se trata.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxctl.h  
  
##  <a name="a-nameafxverifylicfilea--afxverifylicfile"></a><a name="afxverifylicfile"></a>AfxVerifyLicFile  
 Llame a esta función para comprobar que el nombre del archivo de licencia por `pszLicFileName` es válido para el control OLE.  
  
```   
BOOL AFXAPI AfxVerifyLicFile(
    HINSTANCE  hInstance,  
    LPCTSTR  pszLicFileName,  
    LPOLESTR  pszLicFileContents,  
    UINT cch = -1); 
```  
  
### <a name="parameters"></a>Parámetros  
 `hInstance`  
 El identificador de instancia del archivo DLL asociado con el control con licencia.  
  
 `pszLicFileName`  
 Apunta a una cadena de caracteres terminada en null que contiene el nombre de archivo de licencia.  
  
 `pszLicFileContents`  
 Señala a una secuencia de bytes que debe coincidir con la secuencia que se encuentra al principio del archivo de licencia.  
  
 `cch`  
 Número de caracteres de `pszLicFileContents`.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el archivo de licencia existe y comienza con la secuencia de caracteres en `pszLicFileContents`; de lo contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Si `cch` es â €"1, esta función utiliza:  
  
 [!code-cpp[NVC_MFC_Utilities&#36;](../../mfc/codesnippet/cpp/class-factories-and-licensing_2.cpp)]  

### <a name="requirements"></a>Requisitos  
  **Encabezado** afxctl.h  

## <a name="see-also"></a>Vea también  
 [Macros y funciones globales](../../mfc/reference/mfc-macros-and-globals.md)

