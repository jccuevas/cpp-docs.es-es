---
title: Registrar controles OLE | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros.ole
dev_langs:
- C++
helpviewer_keywords:
- registering OLE controls
- OLE controls [MFC], registering
ms.assetid: 73c45b7f-7dbc-43f5-bd17-dd77c6acec72
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4855ca5c461b7437345150f5d199521c48f0b253
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43196558"
---
# <a name="registering-ole-controls"></a>Registrar controles OLE
Pueden tener acceso a los controles OLE, al igual que otros objetos de servidor OLE, por otras aplicaciones compatibles con OLE. Esto se logra mediante el registro de la biblioteca de tipos y la clase del control.  
  
 Las funciones siguientes permiten agregar y quitar la clase del control, páginas de propiedades y biblioteca de tipos en la base de datos de registro de Windows:  
  
### <a name="registering-ole-controls"></a>Registrar controles OLE  
  
|||  
|-|-|  
|[AfxOleRegisterControlClass](#afxoleregistercontrolclass)|La clase del control se agrega a la base de datos de registro.|  
|[AfxOleRegisterPropertyPageClass](#afxoleregisterpropertypageclass)|Agrega una página de propiedades de control a la base de datos de registro.|  
|[AfxOleRegisterTypeLib](#afxoleregistertypelib)|Biblioteca de tipos del control se agrega a la base de datos de registro.|  
|[AfxOleUnregisterClass](#afxoleunregisterclass)|Quita una clase de control o una clase de página de propiedades de la base de datos de registro.|  
|[AfxOleUnregisterTypeLib](#afxoleunregistertypelib)|Quita la biblioteca de tipos del control de la base de datos de registro.|  
  
 `AfxOleRegisterTypeLib` Normalmente se llama en la implementación de un archivo DLL de control de `DllRegisterServer`. De forma similar, `AfxOleUnregisterTypeLib` llama a `DllUnregisterServer`. `AfxOleRegisterControlClass`, `AfxOleRegisterPropertyPageClass`, y `AfxOleUnregisterClass` se suelen denominar simplemente el `UpdateRegistry` función miembro de la página de fábrica o una propiedad de clase del control.  
  
##  <a name="afxoleregistercontrolclass"></a>  AfxOleRegisterControlClass  
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
 *hInstance*  
 El identificador de instancia del módulo asociado a la clase de control.  
  
 *CLSID*  
 El identificador de clase única del control.  
  
 *pszProgID*  
 El identificador único del programa del control.  
  
 *idTypeName*  
 El identificador de recurso de la cadena que contiene un nombre de tipo legible por el usuario para el control.  
  
 *idBitmap*  
 El identificador de recurso de mapa de bits utilizado para representar el control OLE en una barra de herramientas o una paleta.  
  
 *nRegFlags*  
 Contiene uno o varios de los siguientes indicadores:  
  
- `afxRegInsertable` Permite el control aparezca en el cuadro de diálogo Insertar objeto para los objetos OLE.  
  
- `afxRegApartmentThreading` Establece el modelo de subprocesos en el registro para ThreadingModel = apartamento.  
  
- `afxRegFreeThreading` Establece el modelo de subprocesos en el registro para ThreadingModel = gratis.  
  
     Puede combinar las dos marcas `afxRegApartmentThreading` y `afxRegFreeThreading` establecer ThreadingModel = Both. Consulte [InprocServer32](/windows/desktop/com/inprocserver32) en el SDK de Windows para obtener más información sobre el registro del modelo de subprocesos.  
  
> [!NOTE]
>  En las versiones MFC anteriores MFC 4.2, el **int** *nRegFlags* parámetro era un parámetro de tipo BOOL, *bInsertable*, que permite o deniega el control que debe insertarse de la instrucción Insert Cuadro de diálogo del objeto.  
  
 *dwMiscStatus*  
 Contiene uno o varios de los siguientes indicadores de estado (para obtener una descripción de las marcas, vea OLEMISC enumeración en el SDK de Windows):  
  
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
 El identificador único de la clase de control.  
  
 *wVerMajor*  
 El número de versión principal de la clase de control.  
  
 *wVerMinor*  
 El número de versión secundaria de la clase de control.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si se ha registrado la clase del control; en caso contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Esto permite que el control que va a usar contenedores OLE-control. `AfxOleRegisterControlClass` actualiza el registro con el nombre del control y la ubicación en el sistema y también establece el modelo de subprocesos que admite el control en el registro. Para obtener más información, consulte [64 de nota técnica](../../mfc/tn064-apartment-model-threading-in-activex-controls.md), "Subprocesamiento de modelo de subprocesos en controles OLE," y [sobre procesos y subprocesos](/windows/desktop/ProcThread/about-processes-and-threads) en el SDK de Windows.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCAxCtl#11](../../mfc/reference/codesnippet/cpp/registering-ole-controls_1.cpp)]  
  
 El ejemplo anterior se muestra cómo `AfxOleRegisterControlClass` se llama con la marca para insertable y la marca de apartamento ORed juntos para crear el sexto parámetro del modelo:  
  
 [!code-cpp[NVC_MFCAxCtl#12](../../mfc/reference/codesnippet/cpp/registering-ole-controls_2.cpp)]  
  
 El control se mostrará en el cuadro de diálogo Insertar objeto para contenedores habilitados, y será compatible con el modelo de apartamento. Controles compatibles con modelo de apartamento deben asegurarse de esa clase estática datos están protegidos por bloqueos, por lo que mientras un control en un contenedor tiene acceso a los datos estáticos, no se deshabilita el programador antes de que finalice y empieza a usar otra instancia de la misma clase los mismos datos estáticos. Los accesos a los datos estáticos se rodeará por código de sección crítica.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxctl.h  
  
##  <a name="afxoleregisterpropertypageclass"></a>  AfxOleRegisterPropertyPageClass  
 Registra la clase de página de propiedades con la base de datos de registro de Windows.  
  
```  
BOOL AFXAPI AfxOleRegisterPropertyPageClass(
   HINSTANCE hInstance,  
   REFCLSID  clsid,  
   UINT idTypeName,  
   int nRegFlags); 
```  
  
### <a name="parameters"></a>Parámetros  
 *hInstance*  
 El identificador de instancia del módulo asociado con la clase de página de propiedades.  
  
 *CLSID*  
 El identificador de clase única de la página de propiedades.  
  
 *idTypeName*  
 El identificador de recurso de la cadena que contiene un nombre legible por el usuario para la página de propiedades.  
  
 *nRegFlags*  
 Puede contener el indicador:  
  
- `afxRegApartmentThreading` Establece el modelo de subprocesos en el registro para ThreadingModel = apartamento.  
  
> [!NOTE]
>  En las versiones MFC anteriores MFC 4.2, el **int** *nRegFlags* parámetro no estaba disponible. Tenga en cuenta también que el `afxRegInsertable` marca no es una opción válida para páginas de propiedades y provocará una aserción de MFC si se establece  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si se ha registrado la clase del control; en caso contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Esto permite que la página de propiedades que va a usar contenedores OLE-control. `AfxOleRegisterPropertyPageClass` actualiza el registro con el nombre de la página de propiedades y su ubicación en el sistema y también establece el modelo de subprocesos que admite el control en el registro. Para obtener más información, consulte [64 de nota técnica](../../mfc/tn064-apartment-model-threading-in-activex-controls.md), "Subprocesamiento de modelo de subprocesos en controles OLE," y [sobre procesos y subprocesos](/windows/desktop/ProcThread/about-processes-and-threads) en el SDK de Windows.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxctl.h  
  
##  <a name="afxoleregistertypelib"></a>  AfxOleRegisterTypeLib  
 Registra la biblioteca de tipos con la base de datos de registro de Windows y permite que la biblioteca de tipos que va a usar otros contenedores que son compatibles con OLE-control.  
  
```   
BOOL AfxOleRegisterTypeLib(
    HINSTANCE hInstance,  
    REFGUID tlid,  
    LPCTSTR pszFileName = NULL,  
    LPCTSTR pszHelpDir  = NULL); 
```  
  
### <a name="parameters"></a>Parámetros  
 *hInstance*  
 El identificador de instancia de la aplicación asociada con la biblioteca de tipos.  
  
 *tlid*  
 El identificador único de la biblioteca de tipos.  
  
 *pszFileName*  
 Señala al nombre de archivo opcional de una biblioteca de tipos traducida (. Archivo TLB) para el control.  
  
 *pszHelpDir*  
 El nombre del directorio donde se puede encontrar el archivo de ayuda para la biblioteca de tipos. Si es NULL, se supone que el archivo de ayuda en el mismo directorio que la propia biblioteca de tipos.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si se registró la biblioteca de tipos; en caso contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Esta función actualiza el registro con el nombre de la biblioteca de tipos y su ubicación en el sistema.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCAutomation#7](../../mfc/codesnippet/cpp/registering-ole-controls_3.cpp)]  
  
 [!code-cpp[NVC_MFCAutomation#8](../../mfc/codesnippet/cpp/registering-ole-controls_4.cpp)]  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdisp.h  
  
##  <a name="afxoleunregisterclass"></a>  AfxOleUnregisterClass  
 Quita la entrada de clase de página de control o la propiedad de la base de datos de registro de Windows.  
  
```   
BOOL AFXAPI AfxOleUnregisterClass(REFCLSID clsID, LPCSTR pszProgID); 
```  
  
### <a name="parameters"></a>Parámetros  
 *clsID*  
 El identificador de clase única de la página de control o la propiedad.  
  
 *pszProgID*  
 El identificador único del programa de la página de control o la propiedad.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la clase de página de control o la propiedad se ha anulado correctamente; en caso contrario, es 0.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxctl.h  
  
##  <a name="afxoleunregistertypelib"></a>  AfxOleUnregisterTypeLib  
 Llame a esta función para quitar la entrada de la biblioteca de tipo de la base de datos de registro de Windows.  
  
```   
BOOL AFXAPI AfxOleUnregisterTypeLib(REFGUID tlID); 
```  
  
### <a name="parameters"></a>Parámetros  
 *tlID*  
 El identificador único de la biblioteca de tipos.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si se ha anulado correctamente; la biblioteca de tipos en caso contrario, es 0.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCAxCtl#13](../../mfc/reference/codesnippet/cpp/registering-ole-controls_5.cpp)]  

### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdisp.h  

## <a name="see-also"></a>Vea también  
 [Macros y funciones globales](../../mfc/reference/mfc-macros-and-globals.md)
