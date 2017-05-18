---
title: Registrar controles OLE | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.macros.ole
dev_langs:
- C++
helpviewer_keywords:
- registering OLE controls
- OLE controls, registering
ms.assetid: 73c45b7f-7dbc-43f5-bd17-dd77c6acec72
caps.latest.revision: 15
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 17a158366f94d27b7a46917282425d652e6b9042
ms.openlocfilehash: 9c54fb7dc3802e78c8dc68df02ff55ef4732a36b
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="registering-ole-controls"></a>Registrar controles OLE
Controles OLE, como otros objetos de servidor OLE, pueden tener acceso a otras aplicaciones compatible con OLE. Esto se logra registrando la biblioteca de tipos y la clase del control.  
  
 Las funciones siguientes permiten agregar y quitar el control (clase), páginas de propiedades y biblioteca de tipos en la base de datos de registro de Windows:  
  
### <a name="registering-ole-controls"></a>Registrar controles OLE  
  
|||  
|-|-|  
|[AfxOleRegisterControlClass](#afxoleregistercontrolclass)|La clase del control se agrega a la base de datos de registro.|  
|[AfxOleRegisterPropertyPageClass](#afxoleregisterpropertypageclass)|Agrega una página de propiedades de control a la base de datos de registro.|  
|[AfxOleRegisterTypeLib](#afxoleregistertypelib)|Biblioteca de tipos del control se agrega a la base de datos de registro.|  
|[AfxOleUnregisterClass](#afxoleunregisterclass)|Quita una clase de control o una clase de página de propiedades de la base de datos de registro.|  
|[AfxOleUnregisterTypeLib](#afxoleunregistertypelib)|Quita la biblioteca de tipos del control de la base de datos de registro.|  
  
 `AfxOleRegisterTypeLib`Normalmente se llama en la implementación de un archivo DLL de control de `DllRegisterServer`. De forma similar, `AfxOleUnregisterTypeLib` llama a `DllUnregisterServer`. `AfxOleRegisterControlClass`, `AfxOleRegisterPropertyPageClass`, y `AfxOleUnregisterClass` normalmente se llama el `UpdateRegistry` función miembro de la página de fábrica o propiedad de clase de un control.  
  
##  <a name="afxoleregistercontrolclass"></a>AfxOleRegisterControlClass  
 Registra la clase de control con la base de datos de registro de Windows.  
  
```   
BOOL AFXAPI AfxOleRegisterControlClass(
    HINSTANCE hInstance,  
    REFCLSID clsid,  
    LPCTSTR pszProgID,  
    UINT idTypeName,  
    UINT idBitmap,  
    int nRegFlags,  
    DWORD dwMiscStatus,  
    REFGUID tlid,  
    WORD wVerMajor,  
    WORD wVerMinor); 
```  
  
### <a name="parameters"></a>Parámetros  
 `hInstance`  
 El identificador de instancia del módulo asociado a la clase de control.  
  
 `clsid`  
 El identificador de clase único del control.  
  
 `pszProgID`  
 El ID del control.  
  
 `idTypeName`  
 El identificador de recurso de la cadena que contiene un nombre de tipo legible por el usuario para el control.  
  
 *idBitmap*  
 El identificador de recurso de mapa de bits utilizado para representar el control OLE en una barra de herramientas o una paleta.  
  
 `nRegFlags`  
 Contiene uno o varios de los siguientes indicadores:  
  
- `afxRegInsertable`Permite que el control aparezca en el cuadro de diálogo Insertar objeto para los objetos OLE.  
  
- `afxRegApartmentThreading`Establece el modelo de subprocesos en el registro para ThreadingModel = apartamento.  
  
- `afxRegFreeThreading`Establece el modelo de subprocesos en el registro para ThreadingModel = gratis.  
  
     Puede combinar los dos indicadores `afxRegApartmentThreading` y `afxRegFreeThreading` para establecer ThreadingModel = Both. Consulte [InprocServer32](http://msdn.microsoft.com/library/windows/desktop/ms682390) en la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] para obtener más información sobre los subprocesos de registro del modelo.  
  
> [!NOTE]
>  En las versiones MFC anteriores MFC 4.2, el `int` `nRegFlags` parámetro era un **BOOL** parámetro, *bInsertable*, que permite o deniega el control que se va a insertar en el cuadro de diálogo Insertar objeto.  
  
 *dwMiscStatus*  
 Contiene uno o varios de los siguientes indicadores de estado (para obtener una descripción de los indicadores, consulte **OLEMISC** en la enumeración de la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]):  
  
-   OLEMISC_RECOMPOSEONRESIZE  
  
-   OLEMISC_ONLYICONIC  
  
-   OLEMISC_INSERTNOTREPLACE  
  
-   OLEMISC_STATIC  
  
-   OLEMISC_CANTLINKINSIDE  
  
-   OLEMISC_CANLINKBYOLE1  
  
-   OLEMISC_ISLINKOBJECT  
  
-   OLEMISC_INSIDEOUT  
  
-   OLEMISC_ACTIVATEWHENVISIBLE  
  
-   OLEMISC_RENDERINGISDEVICEINDEPENDENT  
  
-   OLEMISC_INVISIBLEATRUNTIME  
  
-   OLEMISC_ALWAYSRUN  
  
-   OLEMISC_ACTSLIKEBUTTON  
  
-   OLEMISC_ACTSLIKELABEL  
  
-   OLEMISC_NOUIACTIVATE  
  
-   OLEMISC_ALIGNABLE  
  
-   OLEMISC_IMEMODE  
  
-   OLEMISC_SIMPLEFRAME  
  
-   OLEMISC_SETCLIENTSITEFIRST  
  
 *tlid*  
 El identificador único de la clase del control.  
  
 `wVerMajor`  
 El número de versión principal de la clase del control.  
  
 `wVerMinor`  
 El número de versión secundaria de la clase del control.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se ha registrado la clase del control; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Esto permite al control se usan los contenedores que están conscientes de control OLE. `AfxOleRegisterControlClass`actualiza el registro con el nombre y la ubicación en el sistema del control y también establece el modelo de subprocesamiento que admite el control en el registro. Para obtener más información, consulte [64 de nota técnica](../../mfc/tn064-apartment-model-threading-in-activex-controls.md), "Modelo de apartamento de subprocesos en controles OLE," y [acerca de procesos y subprocesos](http://msdn.microsoft.com/library/windows/desktop/ms681917) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCAxCtl&#11;](../../mfc/reference/codesnippet/cpp/registering-ole-controls_1.cpp)]  
  
 En el ejemplo anterior se muestra cómo `AfxOleRegisterControlClass` se llama con la marca para insertable y el indicador de apartamento ORed juntos para crear el sexto parámetro de modelo:  
  
 [!code-cpp[NVC_MFCAxCtl&#12;](../../mfc/reference/codesnippet/cpp/registering-ole-controls_2.cpp)]  
  
 El control se mostrará en el cuadro de diálogo Insertar objeto para contenedores habilitados y será compatible con el modelo de apartamento. Controles compatibles con modelo de apartamento deben asegurarse de esa clase estática datos están protegidos por bloqueos, por lo que mientras un control en un contenedor se obtiene acceso a los datos estáticos, no se deshabilita el programador antes de que finalice e inicia otra instancia de la misma clase utilizando los mismos datos estáticos. Los accesos a los datos estáticos se rodeado de código de sección crítica.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxctl.h  
  
##  <a name="afxoleregisterpropertypageclass"></a>AfxOleRegisterPropertyPageClass  
 Registra la clase de página de propiedades con la base de datos de registro de Windows.  
  
```  
BOOL AFXAPI AfxOleRegisterPropertyPageClass(
   HINSTANCE hInstance,  
   REFCLSID  clsid,  
   UINT idTypeName,  
   int nRegFlags); 
```  
  
### <a name="parameters"></a>Parámetros  
 `hInstance`  
 El identificador de instancia del módulo asociado a la clase de página de propiedades.  
  
 `clsid`  
 El identificador de clase único de la página de propiedades.  
  
 `idTypeName`  
 El identificador de recurso de la cadena que contiene un nombre legible para el usuario para la página de propiedades.  
  
 `nRegFlags`  
 Puede contener la marca:  
  
- `afxRegApartmentThreading`Establece el modelo de subprocesos en el registro para ThreadingModel = apartamento.  
  
> [!NOTE]
>  En las versiones MFC anteriores MFC 4.2, el `int` `nRegFlags` parámetro no estaba disponible. Tenga en cuenta también que el `afxRegInsertable` no es una opción válida para páginas de propiedades de marca y provocará una aserción de MFC si se establece  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se ha registrado la clase del control; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Esto permite a la página de propiedades se usan los contenedores que están conscientes de control OLE. `AfxOleRegisterPropertyPageClass`actualiza el registro con el nombre de la página de propiedades y su ubicación en el sistema y también establece el modelo de subprocesamiento que admite el control en el registro. Para obtener más información, consulte [64 de nota técnica](../../mfc/tn064-apartment-model-threading-in-activex-controls.md), "Modelo de apartamento de subprocesos en controles OLE," y [acerca de procesos y subprocesos](http://msdn.microsoft.com/library/windows/desktop/ms681917) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxctl.h  
  
##  <a name="afxoleregistertypelib"></a>AfxOleRegisterTypeLib  
 Registra la biblioteca de tipos con la base de datos de registro de Windows y permite que la biblioteca de tipos que va a usar otros contenedores que están conscientes de control OLE.  
  
```   
BOOL AfxOleRegisterTypeLib(
    HINSTANCE hInstance,  
    REFGUID tlid,  
    LPCTSTR pszFileName = NULL,  
    LPCTSTR pszHelpDir  = NULL); 
```  
  
### <a name="parameters"></a>Parámetros  
 `hInstance`  
 El identificador de instancia de la aplicación asociada a la biblioteca de tipos.  
  
 *tlid*  
 El identificador único de la biblioteca de tipos.  
  
 *pszFileName*  
 Señala al nombre de archivo opcional de una biblioteca de tipos traducida (. Archivo TLB) para el control.  
  
 *pszHelpDir*  
 El nombre del directorio donde se puede encontrar el archivo de ayuda para la biblioteca de tipos. Si **NULL**, se supone que el archivo de ayuda en el mismo directorio que la propia biblioteca de tipo.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se ha registrado la biblioteca de tipos; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Esta función actualiza el registro con el nombre de la biblioteca de tipos y su ubicación en el sistema.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCAutomation&#7;](../../mfc/codesnippet/cpp/registering-ole-controls_3.cpp)]  
  
 [!code-cpp[NVC_MFCAutomation Nº&8;](../../mfc/codesnippet/cpp/registering-ole-controls_4.cpp)]  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdisp.h  
  
##  <a name="afxoleunregisterclass"></a>AfxOleUnregisterClass  
 Quita la entrada de clase de página de control o la propiedad de la base de datos de registro de Windows.  
  
```   
BOOL AFXAPI AfxOleUnregisterClass(REFCLSID clsID, LPCSTR pszProgID); 
```  
  
### <a name="parameters"></a>Parámetros  
 *clsID*  
 El identificador de clase único de la página de control o la propiedad.  
  
 `pszProgID`  
 El identificador único del programa de la página de control o la propiedad.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la clase de página de propiedad o se anuló correctamente el registro; en caso contrario, 0.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxctl.h  
  
##  <a name="afxoleunregistertypelib"></a>AfxOleUnregisterTypeLib  
 Llame a esta función para quitar la entrada de la biblioteca de tipos de la base de datos de registro de Windows.  
  
```   
BOOL AFXAPI AfxOleUnregisterTypeLib(REFGUID tlID); 
```  
  
### <a name="parameters"></a>Parámetros  
 `tlID`  
 El identificador único de la biblioteca de tipos.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la biblioteca de tipos se anuló correctamente el registro; en caso contrario, 0.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCAxCtl&#13;](../../mfc/reference/codesnippet/cpp/registering-ole-controls_5.cpp)]  

### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdisp.h  

## <a name="see-also"></a>Vea también  
 [Macros y funciones globales](../../mfc/reference/mfc-macros-and-globals.md)

