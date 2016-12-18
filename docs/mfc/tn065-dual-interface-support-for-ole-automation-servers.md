---
title: "TN065: Compatibilidad con una interfaz dual para los servidores de automatizaci&#243;n OLE | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.ole"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ACDUAL (ejemplo) [MFC]"
  - "servidores de automatización, compatibilidad con interfaz dual"
  - "interfaces duales, automatización OLE"
  - "TN065"
ms.assetid: b5c8ed09-2f7f-483c-80fc-2a47ad896063
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN065: Compatibilidad con una interfaz dual para los servidores de automatizaci&#243;n OLE
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea.  Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos.  Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.  
  
 Esta nota explica cómo agregar compatibilidad con la dual\- interfaz a una aplicación de servidor MFC\- basada de automatización OLE.  El ejemplo de [ACDUAL](../top/visual-cpp-samples.md) muestra compatibilidad con la dual\- interfaz, y el código de ejemplo de esta nota se toma ACDUAL.  Las macros descritas en esta nota, como `DECLARE_DUAL_ERRORINFO`, `DUAL_ERRORINFO_PART`, y `IMPLEMENT_DUAL_ERRORINFO`, forman parte del ejemplo ACDUAL y se encuentran en MFCDUAL.H.  
  
## Interfaces duales  
 Aunque la automatización OLE permite implementar una interfaz de `IDispatch` , una interfaz de VTBL, o una interfaz dual \(que abarca ambos\), Microsoft recomienda implementar interfaces duales para todos los objetos de automatización OLE expuestos.  Las interfaces duales tienen ventajas significativas en `IDispatch`\- solo o las interfaces de VTBL\-only:  
  
-   El enlace puede tener lugar en tiempo de compilación a través de la interfaz de VTBL, o en tiempo de ejecución con `IDispatch`.  
  
-   Los controladores de automatización OLE que pueden utilizar la interfaz de VTBL pueden beneficiarse de rendimiento mejorado.  
  
-   Los controladores existentes de automatización OLE que utilizan la interfaz de `IDispatch` continuarán funcionando.  
  
-   La interfaz de VTBL es más fácil de llamar desde C\+\+.  
  
-   Las interfaces duales se requieren para la compatibilidad con las características de compatibilidad del objeto de Visual Basic.  
  
## Compatibilidad con la Dual\- interfaz a una clase CCmdTarget\- basada  
 Una interfaz dual es simplemente una interfaz personalizada derivada de `IDispatch`.  La manera más sencilla de implementar la compatibilidad de la dual\- interfaz en `CCmdTarget`\- clase basada a primero implementa la interfaz de distribución normal en la clase mediante y MFC ClassWizard, le agrega la interfaz personalizada más adelante.  En general, la implementación personalizada de la interfaz delegará simplemente a MFC `IDispatch` la implementación.  
  
 Primero, modifique el archivo ODL para que el servidor defina interfaces duales para objetos.  Para definir una interfaz dual, debe utilizar una instrucción interface, en lugar de la instrucción de `DISPINTERFACE` que los asistentes de Visual C\+\+ generan.  En lugar de quitar la instrucción existente de `DISPINTERFACE` , agregue una nueva instrucción interface.  Mantener el formulario de `DISPINTERFACE` , puede seguir utilizando ClassWizard para agregar propiedades y métodos del objeto, pero debe agregar propiedades y métodos equivalentes a la instrucción interface.  
  
 Una instrucción de interfaz para una interfaz dual debe tener los atributos de **OLEAUTOMATION** y de **DUAL** , y se debe derivar de `IDispatch`.  Puede utilizar el ejemplo de [GUIDGEN](../top/visual-cpp-samples.md) para crear **IID** para la interfaz dual:  
  
```  
[ uuid(0BDD0E81-0DD7-11cf-BBA8-444553540000), // IID_IDualAClick  
   oleautomation,  
   dual  
]  
interface IDualAClick : IDispatch  
  {  
  };  
```  
  
 Una vez que tenga la instrucción interface, iniciar las entradas de suma para los métodos y propiedades.  Para interfaces duales, necesita reorganizar las listas de parámetros de modo que los métodos y las funciones del descriptor de acceso de la propiedad en la interfaz dual devuelven `HRESULT` y pasan los valores devueltos como parámetros con atributos `[retval,out]`.  Recuerde que para las propiedades, necesitará agregar una lectura \(`propget`\) y la función de acceso de escritura \(`propput`\) con la misma identificación  Por ejemplo:  
  
```  
[propput, id(1)] HRESULT text([in] BSTR newText);  
[propget, id(1)] HRESULT text([out, retval] BSTR* retval);  
```  
  
 Después de los métodos y las propiedades se definen, necesita agregar una referencia a la instrucción de interfaz en la instrucción coclass.  Por ejemplo:  
  
```  
[ uuid(4B115281-32F0-11cf-AC85-444553540000) ]  
coclass Document  
{  
   dispinterface IAClick;  
   [default] interface IDualAClick;  
};  
```  
  
 Una vez que se ha actualizado el archivo ODL, utilice el mecanismo de asignación de la interfaz de MFC para definir una clase de implementación de la interfaz dual en la clase de objeto y crear las entradas correspondientes en el mecanismo de `QueryInterface` MFC.  Necesita una entrada en `INTERFACE_PART` bloqueado para cada entrada de la instrucción de la interfaz de ODL, más las entradas para una interfaz de envío.  Cada entrada ODL con el atributo de **propput** necesita una función denominada `put_propertyname`.  Cada entrada con el atributo de **propget** necesita una función denominada `get_propertyname`.  
  
 Para definir una clase de implementación de la interfaz dual, agregue `DUAL_INTERFACE_PART` bloqueado a la definición de clase de objeto.  Por ejemplo:  
  
```  
BEGIN_DUAL_INTERFACE_PART(DualAClick, IDualAClick)  
  STDMETHOD(put_text)(THIS_ BSTR newText);  
  STDMETHOD(get_text)(THIS_ BSTR FAR* retval);  
  STDMETHOD(put_x)(THIS_ short newX);  
  STDMETHOD(get_x)(THIS_ short FAR* retval);  
  STDMETHOD(put_y)(THIS_ short newY);  
  STDMETHOD(get_y)(THIS_ short FAR* retval);  
  STDMETHOD(put_Position)(THIS_ IDualAutoClickPoint FAR* newPosition);  
  STDMETHOD(get_Position)(THIS_ IDualAutoClickPoint FAR* FAR* retval);  
  STDMETHOD(RefreshWindow)(THIS);  
  STDMETHOD(SetAllProps)(THIS_ short x, short y, BSTR text);  
  STDMETHOD(ShowWindow)(THIS);  
END_DUAL_INTERFACE_PART(DualAClick)  
```  
  
 Para conectar la interfaz dual al mecanismo de [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms687230) de MFC, agregue una entrada de `INTERFACE_PART` a la interfaz asignada:  
  
```  
BEGIN_INTERFACE_MAP(CAutoClickDoc, CDocument)  
  INTERFACE_PART(CAutoClickDoc, DIID_IAClick, Dispatch)  
  INTERFACE_PART(CAutoClickDoc, IID_IDualAClick, DualAClick)  
END_INTERFACE_MAP()  
```  
  
 A continuación, debe completar la implementación de la interfaz.  En general, podrá delegar a MFC `IDispatch` la implementación existente.  Por ejemplo:  
  
```  
STDMETHODIMP_(ULONG) CAutoClickDoc::XDualAClick::AddRef()  
{  
   METHOD_PROLOGUE(CAutoClickDoc, DualAClick)  
   return pThis->ExternalAddRef();  
}  
STDMETHODIMP_(ULONG) CAutoClickDoc::XDualAClick::Release()  
{  
   METHOD_PROLOGUE(CAutoClickDoc, DualAClick)  
   return pThis->ExternalRelease();  
}  
STDMETHODIMP CAutoClickDoc::XDualAClick::QueryInterface(  
             REFIID iid, LPVOID* ppvObj)  
{  
   METHOD_PROLOGUE(CAutoClickDoc, DualAClick)  
   return pThis->ExternalQueryInterface(&iid, ppvObj);  
}  
STDMETHODIMP CAutoClickDoc::XDualAClick::GetTypeInfoCount(  
            UINT FAR* pctinfo)  
{  
   METHOD_PROLOGUE(CAutoClickDoc, DualAClick)  
   LPDISPATCH lpDispatch = pThis->GetIDispatch(FALSE);  
   ASSERT(lpDispatch != NULL);  
   return lpDispatch->GetTypeInfoCount(pctinfo);  
}  
STDMETHODIMP CAutoClickDoc::XDualAClick::GetTypeInfo(  
          UINT itinfo, LCID lcid, ITypeInfo FAR* FAR* pptinfo)  
{  
   METHOD_PROLOGUE(CAutoClickDoc, DualAClick)  
   LPDISPATCH lpDispatch = pThis->GetIDispatch(FALSE);  
   ASSERT(lpDispatch != NULL);  
   return lpDispatch->GetTypeInfo(itinfo, lcid, pptinfo);  
}  
STDMETHODIMP CAutoClickDoc::XDualAClick::GetIDsOfNames(  
       REFIID riid, OLECHAR FAR* FAR* rgszNames, UINT cNames,  
       LCID lcid, DISPID FAR* rgdispid)   
{  
   METHOD_PROLOGUE(CAutoClickDoc, DualAClick)  
   LPDISPATCH lpDispatch = pThis->GetIDispatch(FALSE);  
   ASSERT(lpDispatch != NULL);  
   return lpDispatch->GetIDsOfNames(riid, rgszNames, cNames,   
                                    lcid, rgdispid);  
}  
STDMETHODIMP CAutoClickDoc::XDualAClick::Invoke(  
    DISPID dispidMember, REFIID riid, LCID lcid, WORD wFlags,  
    DISPPARAMS FAR* pdispparams, VARIANT FAR* pvarResult,  
    EXCEPINFO FAR* pexcepinfo, UINT FAR* puArgErr)  
{  
   METHOD_PROLOGUE(CAutoClickDoc, DualAClick)  
   LPDISPATCH lpDispatch = pThis->GetIDispatch(FALSE);  
   ASSERT(lpDispatch != NULL);  
   return lpDispatch->Invoke(dispidMember, riid, lcid,  
                             wFlags, pdispparams, pvarResult,  
                             pexcepinfo, puArgErr);  
}  
```  
  
 Para los métodos de objetos y las funciones del descriptor de propiedad, deberá completar la implementación.  Las funciones de métodos y propiedades pueden delegar normalmente a los métodos generados mediante ClassWizard.  Sin embargo, si las propiedades de configuración para tener acceso a variables directamente, debe escribir el código para obtener y coloque el valor de la variable.  Por ejemplo:  
  
```  
STDMETHODIMP CAutoClickDoc::XDualAClick::put_text(BSTR newText)  
{  
   METHOD_PROLOGUE(CAutoClickDoc, DualAClick)  
   // MFC automatically converts from Unicode BSTR to   
   // Ansi CString, if necessary...  
   pThis->m_str = newText;  
   return NOERROR;  
}  
STDMETHODIMP CAutoClickDoc::XDualAClick::get_text(BSTR* retval)  
{  
   METHOD_PROLOGUE(CAutoClickDoc, DualAClick)  
   // MFC automatically converts from Ansi CString to   
   // Unicode BSTR, if necessary...  
   pThis->m_str.SetSysString(retval);  
   return NOERROR;  
}  
```  
  
## Punteros de la Dual\- interfaz  
 Pasar el puntero de la dual\- interfaz no es sencillo, especialmente si necesita llamar `CCmdTarget::FromIDispatch`.  `FromIDispatch` sólo funciona en los punteros de `IDispatch` MFC.  Una forma de evitar este es consultar la configuración original del puntero de `IDispatch` por MFC y pasar ese puntero a funciones que lo necesitan.  Por ejemplo:  
  
```  
STDMETHODIMP CAutoClickDoc::XDualAClick::put_Position(  
      IDualAutoClickPoint FAR* newPosition)  
{  
   METHOD_PROLOGUE(CAutoClickDoc, DualAClick)  
   LPDISPATCH lpDisp = NULL;  
   newPosition->QueryInterface(IID_IDispatch, (LPVOID*)&lpDisp);  
   pThis->SetPosition(lpDisp);  
   lpDisp->Release();  
   return NOERROR;  
}  
```  
  
 Antes de pasar una reproducción de puntero con el método de la dual\- interfaz, puede ser necesario convertirlo de puntero de MFC `IDispatch` al puntero de la dual\- interfaz.  Por ejemplo:  
  
```  
STDMETHODIMP CAutoClickDoc::XDualAClick::get_Position(  
      IDualAutoClickPoint FAR* FAR* retval)  
{  
   METHOD_PROLOGUE(CAutoClickDoc, DualAClick)  
   LPDISPATCH lpDisp;  
   lpDisp = pThis->GetPosition();  
   lpDisp->QueryInterface(IID_IDualAutoClickPoint, (LPVOID*)retval);  
   return NOERROR;  
}  
```  
  
## Registrar la biblioteca de tipos de la aplicación  
 AppWizard no genera código para registrar la biblioteca de tipos de una aplicación de servidor de automatización OLE en el sistema.  Cuando hay otras maneras de registrar la biblioteca de tipos, deben tener el registro de la aplicación de la biblioteca de tipos cuando se actualiza la información de tipo OLE, es decir, siempre que la aplicación sea independiente ejecutado.  
  
 Para registrar la biblioteca de tipos de la aplicación cada vez que la aplicación sea compatibilidad ejecutado solo:  
  
-   Inclusión AFXCTL.H en el estándar incluye el archivo de encabezado, STDAFX.H, para tener acceso a la definición de la función de `AfxOleRegisterTypeLib` .  
  
-   En función de `InitInstance` de la aplicación, busque la llamada a `COleObjectFactory::UpdateRegistryAll`.  Después de esta llamada, agregue una llamada a `AfxOleRegisterTypeLib`, especificando **LIBID** correspondiente a la biblioteca de tipos, junto con el nombre de la biblioteca de tipos:  
  
    ```  
    // When a server application is launched stand-alone, it is a good idea  
    // to update the system registry in case it has been damaged.  
    m_server.UpdateRegistry(OAT_DISPATCH_OBJECT);  
    COleObjectFactory::UpdateRegistryAll();  
    // DUAL_SUPPORT_START  
    // Make sure the type library is registered or dual interface won't work.  
    AfxOleRegisterTypeLib(AfxGetInstanceHandle(), LIBID_ACDual, _T("AutoClik.TLB"));  
    // DUAL_SUPPORT_END  
    ```  
  
## Modificar la configuración de compilación del proyecto para acomodar los cambios de la biblioteca de tipos  
 Para modificar la configuración de compilación de un proyecto para que un archivo de encabezado que contiene las definiciones de **UUID** es generado por MkTypLib siempre que se recompile la biblioteca de tipos:  
  
1.  En el menú de **Compilación** , haga clic en **Configuración**, y seleccione el archivo ODL de la lista de archivos para cada configuración.  
  
2.  Haga clic en la pestaña de **OLE Types** y especifique un nombre de archivo en el campo de nombre de archivo de **Output header** .  Utilice un nombre de archivo que no es ya usado por proyecto, porque MkTypLib sobrescribirá cualquier archivo existente.  Haga clic en **Aceptar** para cerrar el cuadro de diálogo de **Configuración de compilación** .  
  
 Para agregar las definiciones de **UUID** del archivo de encabezado MkTypLib\- generado al proyecto:  
  
1.  Incluya el archivo de encabezado MkTypLib\- generado en el estándar incluye el archivo de encabezado, STDAFX.H.  
  
2.  Cree un nuevo archivo, INITIIDS.CPP, y agréguelo al proyecto.  En este archivo, incluya el archivo de encabezado MkTypLib\- generado después de incluir OLE2.H e INITGUID.H:  
  
    ```  
    // initIIDs.c: defines IIDs for dual interfaces  
    // This must not be built with precompiled header.  
      #include <ole2.h>  
      #include <initguid.h>  
      #include "acdual.h"  
    ```  
  
3.  En el menú de **Compilación** , haga clic en **Configuración**, y el INITIIDS.CPP seleccione en la lista de archivos para cada configuración.  
  
4.  Haga clic en la pestaña de **C\+\+** , haga clic en la categoría **Encabezados precompilados**, y seleccione el botón de opción de **No utilizar encabezados precompilados** .  Haga clic en aceptar para cerrar el cuadro de diálogo de **Configuración de compilación** .  
  
## Especificar el nombre de clase de objeto correcto en la biblioteca de tipos  
 Los asistentes incluidos con Visual C\+\+ utilizan incorrectamente el nombre de clase de implementación para especificar la coclase del archivo de ODL de servidor para las clases OLE \- pueden crearse.  Mientras que esto, el nombre de clase de implementación probablemente no es el nombre de clase que desea que los usuarios del objeto para uso.  Para especificar el nombre correcto, abrir el archivo ODL, buscar cada instrucción coclass, y reemplazar el nombre de clase de implementación con el nombre externo correcto.  
  
 Observe que cuando la instrucción coclass, los nombres de variable de s para **CLSID**en el archivo de encabezado MkTypLib\- generado cambiarán en consecuencia.  Deberá actualizar el código para usar los nuevos nombres de variable.  
  
## Administrar Excepciones y las interfaces de error de automatización  
 Los métodos de objetos de automatización y las funciones del descriptor de propiedad pueden producir excepciones.  Si es así debe controlarlos en la implementación de la dual\- interfaz y devolver información sobre la excepción el controlador a través de la interfaz de control de errores de automatización OLE, **IErrorInfo**.  Esta interfaz proporciona información detallada sobre errores, contextual a través de `IDispatch` e interfaces de VTBL.  Para indicar que un controlador de errores está disponible, debe implementar la interfaz de **ISupportErrorInfo** .  
  
 Para mostrar el mecanismo de control de errores, supongamos que las funciones ClassWizard\- generadas utilizadas para implementar las excepciones estándar throw de soporte de envío.  Implementación de MFC de **IDispatch::Invoke** detecta normalmente estas excepciones y las convierte en una estructura de EXCEPTINFO que se devuelve con la llamada de `Invoke` .  Sin embargo, cuando se utiliza la interfaz de VTBL, es responsable de detectar las excepciones usted mismo.  Como ejemplo de proteger los métodos de la dual\-interfaz:  
  
```  
STDMETHODIMP CAutoClickDoc::XDualAClick::put_text(BSTR newText)  
{  
   METHOD_PROLOGUE(CAutoClickDoc, DualAClick)  
   TRY_DUAL(IID_IDualAClick)  
   {  
      // MFC automatically converts from Unicode BSTR to   
      // Ansi CString, if necessary...  
      pThis->m_str = newText;  
      return NOERROR;  
   }  
   CATCH_ALL_DUAL  
}  
```  
  
 `CATCH_ALL_DUAL` se ocupa de devolver el código de error correcto cuando se produce una excepción.  `CATCH_ALL_DUAL` convierte una excepción de MFC del control de errores de automatización OLE mediante la interfaz de **ICreateErrorInfo** . \(Una macro de `CATCH_ALL_DUAL` de ejemplo está en el archivo MFCDUAL.H en el ejemplo de [ACDUAL](../top/visual-cpp-samples.md) .  La función que llama para controlar las excepciones, `DualHandleException`, está en el archivo MFCDUAL.CPP.\) `CATCH_ALL_DUAL` determina el código de error retorno según el tipo de excepción que provocó:  
  
-   [COleDispatchException](../mfc/reference/coledispatchexception-class.md) – In This Case, `HRESULT` se construye utilizando el código siguiente:  
  
    ```  
    hr = MAKE_HRESULT(SEVERITY_ERROR, FACILITY_ITF,   
                               (e->m_wCode + 0x200));  
    ```  
  
     Esto crea un específico de `HRESULT` a la interfaz que produjo la excepción.  El código de error es de desplazamiento por 0x200 para evitar cualquier conflicto con s sistema\- definido de `HRESULT`para las interfaces VIEJAS estándar.  
  
-   [CMemoryException](../mfc/reference/cmemoryexception-class.md) – se devuelve In This Case, `E_OUTOFMEMORY` .  
  
-   Cualquier otra excepción – se devuelve In This Case, `E_UNEXPECTED` .  
  
 Para indicar que utilizan el controlador de errores de automatización OLE, también debe implementar la interfaz de **ISupportErrorInfo** .  
  
 Primero, agregue el código a la definición de clase de automatización para mostrarla que admite **ISupportErrorInfo**.  
  
 En segundo lugar, agregue el código a la interfaz de clase de automatización asignada para asociar la clase de implementación de **ISupportErrorInfo** con el mecanismo de `QueryInterface` MFC.  Las coincidencias de la instrucción de `INTERFACE_PART` que la clase definido para **ISupportErrorInfo**.  
  
 Finalmente, implemente la clase definida para admitir **ISupportErrorInfo**.  
  
 \(Ejemplo de El [ACDUAL](../top/visual-cpp-samples.md) contiene tres macros para ayudar a estos tres pasos, `DECLARE_DUAL_ERRORINFO`, `DUAL_ERRORINFO_PART`, y `IMPLEMENT_DUAL_ERRORINFO`, contenido todo en MFCDUAL.H.\)  
  
 El ejemplo siguiente implementa una clase definida para admitir **ISupportErrorInfo**.  `CAutoClickDoc` es el nombre de la clase de automatización y `IID_IDualAClick` es **IID** para la interfaz que es el origen de los errores detectados a través del objeto de error de automatización OLE:  
  
```  
STDMETHODIMP_(ULONG) CAutoClickDoc::XSupportErrorInfo::AddRef()   
{  
   METHOD_PROLOGUE(CAutoClickDoc, SupportErrorInfo)   
   return pThis->ExternalAddRef();   
}   
STDMETHODIMP_(ULONG) CAutoClickDoc::XSupportErrorInfo::Release()   
{   
   METHOD_PROLOGUE(CAutoClickDoc, SupportErrorInfo)   
   return pThis->ExternalRelease();   
}   
STDMETHODIMP CAutoClickDoc::XSupportErrorInfo::QueryInterface(   
   REFIID iid, LPVOID* ppvObj)   
{   
   METHOD_PROLOGUE(CAutoClickDoc, SupportErrorInfo)   
   return pThis->ExternalQueryInterface(&iid, ppvObj);   
}   
STDMETHODIMP CAutoClickDoc::XSupportErrorInfo::InterfaceSupportsErrorInfo(   
   REFIID iid)   
{   
   METHOD_PROLOGUE(CAutoClickDoc, SupportErrorInfo)   
   return (iid == IID_IDualAClick) ? S_OK : S_FALSE;   
}  
```  
  
## Vea también  
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)