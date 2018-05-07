---
title: 'TN065: Compatibilidad de interfaz Dual para los servidores de automatización OLE | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.ole
dev_langs:
- C++
helpviewer_keywords:
- dual interfaces [MFC], OLE Automation
- TN065 [MFC]
- ACDUAL sample [MFC]
- Automation servers [MFC], dual-interface support
ms.assetid: b5c8ed09-2f7f-483c-80fc-2a47ad896063
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3b1c0d30938529d9eb432e6171b546a42f87905a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="tn065-dual-interface-support-for-ole-automation-servers"></a>TN065: Compatibilidad con una interfaz dual para los servidores de Automation OLE
> [!NOTE]
>  La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea. Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos. Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.  
  
 Esta nota describe cómo agregar compatibilidad con una interfaz dual a una aplicación de servidor basada en MFC automatización OLE. El [ACDUAL](../visual-cpp-samples.md) ejemplo muestra la compatibilidad con una interfaz dual, y el código de ejemplo en esta nota se realiza desde ACDUAL. Las macros que se describe en este sentido, como `DECLARE_DUAL_ERRORINFO`, `DUAL_ERRORINFO_PART`, y `IMPLEMENT_DUAL_ERRORINFO`, forman parte del ejemplo ACDUAL y puede encontrarse en MFCDUAL. H.  
  
## <a name="dual-interfaces"></a>Interfaces duales  
 Aunque OLE Automation le permite implementar una `IDispatch` interfaz, una interfaz VTBL o una interfaz dual (que incluye ambos), Microsoft recomienda encarecidamente implementar interfaces duales para todos los objetos de automatización OLE de expuesto. Interfaces duales tienen ventajas importantes sobre `IDispatch`-únicas o VTBL interfaces:  
  
-   Enlace puede tener lugar en tiempo de compilación a través de la interfaz VTBL o en tiempo de ejecución a través de `IDispatch`.  
  
-   Los controladores de automatización OLE que se pueden utilizar la interfaz VTBL pueden beneficiarse de mejorar el rendimiento.  
  
-   Los controladores de automatización OLE existentes que usan la `IDispatch` interfaz continuarán funcionando.  
  
-   La interfaz VTBL es más fácil llamar desde C++.  
  
-   Interfaces duales son necesarias para la compatibilidad con características de compatibilidad de objeto de Visual Basic.  
  
## <a name="adding-dual-interface-support-to-a-ccmdtarget-based-class"></a>Agregar compatibilidad de interfaz Dual para una clase basada en CCmdTarget  
 Una interfaz dual es simplemente una interfaz personalizada que deriva de `IDispatch`. La manera más sencilla de implementar la compatibilidad con interfaz dual en una `CCmdTarget`-basado en clase consiste en implementar primero la distribución normal de la interfaz en la clase mediante MFC y ClassWizard, a continuación, agregue la interfaz personalizada más adelante. En su mayor parte, la implementación de interfaz personalizada simplemente delegarán hacia la MFC `IDispatch` implementación.  
  
 En primer lugar, modifique el archivo ODL para el servidor definir las interfaces duales para los objetos. Para definir una interfaz dual, debe utilizar una instrucción de interfaz, en lugar de la `DISPINTERFACE` instrucción que generan los asistentes de Visual C++. En lugar de quitar las existentes `DISPINTERFACE` (instrucción), agregue una nueva instrucción de interfaz. Al conservar la `DISPINTERFACE` formulario, aún puede usar Asistente para agregar propiedades y métodos al objeto, pero debe agregar los métodos y propiedades equivalentes a su declaración de interfaz.  
  
 Debe tener una declaración de interfaz de una interfaz dual el **OLEAUTOMATION** y **DUAL** atributos y la interfaz se deben derivar de `IDispatch`. Puede usar el [GUIDGEN](../visual-cpp-samples.md) ejemplo para crear un **IID** para la interfaz dual:  
  
```  
[ uuid(0BDD0E81-0DD7-11cf-BBA8-444553540000), // IID_IDualAClick  
    oleautomation, 
    dual 
]  
interface IDualAClick : IDispatch  
 {  
 };  
```  
  
 Una vez que la instrucción de la interfaz en su lugar, empezar a agregar entradas para los métodos y propiedades. Para interfaces duales, debe volver a organizar las listas de parámetros para que los métodos y las funciones de descriptor de acceso de propiedad en la interfaz dual devuelven un `HRESULT` y pasar sus valores devueltos como parámetros con los atributos `[retval,out]`. Recuerde que para las propiedades, debe agregar una lectura (`propget`) y escritura (`propput`) tener acceso a la función con el mismo identificador. Por ejemplo:  
  
```  
[propput,
    id(1)] HRESULT text([in] BSTR newText);

[propget,
    id(1)] HRESULT text([out,
    retval] BSTR* retval);
```  
  
 Después de que se definen los métodos y propiedades, debe agregar una referencia a la instrucción de la interfaz en la instrucción de la coclase. Por ejemplo:  
  
```  
[ uuid(4B115281-32F0-11cf-AC85-444553540000) ]  
coclass Document  
{  
    dispinterface IAClick;  
 [default] interface IDualAClick;  
};  
```  
  
 Una vez que se ha actualizado el archivo ODL, utilice el mecanismo de mapa de interfaz de MFC para definir una clase de implementación para la interfaz dual en la clase de objeto y establecer las entradas correspondientes de MFC `QueryInterface` mecanismo. Necesita una entrada en el `INTERFACE_PART` bloque para cada entrada de la instrucción de la interfaz de la ODL, además de las entradas de una interfaz de envío. Cada entrada ODL con el **propput** atributo tiene una función denominada `put_propertyname`. Cada entrada con la **propget** atributo tiene una función denominada `get_propertyname`.  
  
 Para definir una clase de implementación para la interfaz dual, agregue un `DUAL_INTERFACE_PART` bloque a la definición de clase de objeto. Por ejemplo:  
  
```  
BEGIN_DUAL_INTERFACE_PART(DualAClick,
    IDualAClick)  
    STDMETHOD(put_text)(THIS_ BSTR newText);

    STDMETHOD(get_text)(THIS_ BSTR FAR* retval);

    STDMETHOD(put_x)(THIS_ short newX);

    STDMETHOD(get_x)(THIS_ short FAR* retval);

    STDMETHOD(put_y)(THIS_ short newY);

    STDMETHOD(get_y)(THIS_ short FAR* retval);

    STDMETHOD(put_Position)(THIS_ IDualAutoClickPoint FAR* newPosition);

    STDMETHOD(get_Position)(THIS_ IDualAutoClickPoint FAR* FAR* retval);

    STDMETHOD(RefreshWindow)(THIS);

 STDMETHOD(SetAllProps)(THIS_ short x,
    short y,
    BSTR text);

    STDMETHOD(ShowWindow)(THIS);

END_DUAL_INTERFACE_PART(DualAClick) 
```  
  
 Para conectar la interfaz dual para de MFC [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms687230) mecanismo, agregue un `INTERFACE_PART` entrada para el mapa de interfaz:  
  
```  
BEGIN_INTERFACE_MAP(CAutoClickDoc,
    CDocument)  
    INTERFACE_PART(CAutoClickDoc,
    DIID_IAClick,
    Dispatch)  
    INTERFACE_PART(CAutoClickDoc,
    IID_IDualAClick,
    DualAClick)  
END_INTERFACE_MAP()  
```  
  
 A continuación, debe rellenar la implementación de la interfaz. En su mayor parte, podrá delegar a MFC existente `IDispatch` implementación. Por ejemplo:  
  
```  
STDMETHODIMP_(ULONG) CAutoClickDoc::XDualAClick::AddRef()  
{  
    METHOD_PROLOGUE(CAutoClickDoc,
    DualAClick)  
    return pThis->ExternalAddRef();

}  
STDMETHODIMP_(ULONG) CAutoClickDoc::XDualAClick::Release()  
{  
    METHOD_PROLOGUE(CAutoClickDoc,
    DualAClick)  
    return pThis->ExternalRelease();

}  
STDMETHODIMP CAutoClickDoc::XDualAClick::QueryInterface(
    REFIID iid,
    LPVOID* ppvObj)  
{  
    METHOD_PROLOGUE(CAutoClickDoc,
    DualAClick)  
    return pThis->ExternalQueryInterface(&iid,
    ppvObj);

}  
STDMETHODIMP CAutoClickDoc::XDualAClick::GetTypeInfoCount(
    UINT FAR* pctinfo)  
{  
    METHOD_PROLOGUE(CAutoClickDoc,
    DualAClick)  
    LPDISPATCH lpDispatch = pThis->GetIDispatch(FALSE);

    ASSERT(lpDispatch != NULL);

    return lpDispatch->GetTypeInfoCount(pctinfo);

}  
STDMETHODIMP CAutoClickDoc::XDualAClick::GetTypeInfo(
    UINT itinfo,
    LCID lcid,
    ITypeInfo FAR* FAR* pptinfo)  
{  
    METHOD_PROLOGUE(CAutoClickDoc,
    DualAClick)  
    LPDISPATCH lpDispatch = pThis->GetIDispatch(FALSE);

    ASSERT(lpDispatch != NULL);

    return lpDispatch->GetTypeInfo(itinfo,
    lcid,
    pptinfo);

}  
STDMETHODIMP CAutoClickDoc::XDualAClick::GetIDsOfNames(
    REFIID riid,
    OLECHAR FAR* FAR* rgszNames,
    UINT cNames,  
    LCID lcid,
    DISPID FAR* rgdispid)   
{  
    METHOD_PROLOGUE(CAutoClickDoc,
    DualAClick)  
    LPDISPATCH lpDispatch = pThis->GetIDispatch(FALSE);

    ASSERT(lpDispatch != NULL);

    return lpDispatch->GetIDsOfNames(riid,
    rgszNames,
    cNames,   
    lcid,
    rgdispid);

}  
STDMETHODIMP CAutoClickDoc::XDualAClick::Invoke(
    DISPID dispidMember,
    REFIID riid,
    LCID lcid,
    WORD wFlags,  
    DISPPARAMS FAR* pdispparams,
    VARIANT FAR* pvarResult,  
    EXCEPINFO FAR* pexcepinfo,
    UINT FAR* puArgErr)  
{  
    METHOD_PROLOGUE(CAutoClickDoc,
    DualAClick)  
    LPDISPATCH lpDispatch = pThis->GetIDispatch(FALSE);

    ASSERT(lpDispatch != NULL);

    return lpDispatch->Invoke(dispidMember,
    riid,
    lcid,  
    wFlags,
    pdispparams,
    pvarResult,  
    pexcepinfo,
    puArgErr);

}  
```  
  
 Para los métodos y las funciones de descriptor de acceso de propiedad del objeto, debe rellenar la implementación. Las funciones de método y propiedad por lo general pueden delegar a los métodos generados mediante el asistente. Sin embargo, si establece las propiedades para tener acceso directamente a las variables, debe escribir el código para obtener o colocar el valor en la variable. Por ejemplo:  
  
```  
STDMETHODIMP CAutoClickDoc::XDualAClick::put_text(BSTR newText)  
{  
    METHOD_PROLOGUE(CAutoClickDoc,
    DualAClick) *// MFC automatically converts from Unicode BSTR to *// Ansi CString,
    if necessary...  
    pThis->m_str = newText;  
    return NOERROR;  
}  
STDMETHODIMP CAutoClickDoc::XDualAClick::get_text(BSTR* retval)  
{  
    METHOD_PROLOGUE(CAutoClickDoc,
    DualAClick) *// MFC automatically converts from Ansi CString to *// Unicode BSTR,
    if necessary...  
    pThis->m_str.SetSysString(retval);

 return NOERROR;  
}  
```  
  
## <a name="passing-dual-interface-pointers"></a>Pasar punteros de interfaz Dual  
 Si se pasa el puntero de interfaz dual no es sencillo, especialmente si tiene que llamar a `CCmdTarget::FromIDispatch`. `FromIDispatch` solo funciona en de MFC `IDispatch` punteros. Una manera de solucionar este problema es para consultar la versión original `IDispatch` puntero conjunto una copia de seguridad por MFC y pasar ese puntero a funciones que lo necesitan. Por ejemplo:  
  
```  
STDMETHODIMP CAutoClickDoc::XDualAClick::put_Position(
    IDualAutoClickPoint FAR* newPosition)  
{  
    METHOD_PROLOGUE(CAutoClickDoc,
    DualAClick)  
    LPDISPATCH lpDisp = NULL;  
    newPosition->QueryInterface(IID_IDispatch, (LPVOID*)&lpDisp);

    pThis->SetPosition(lpDisp);

 lpDisp->Release();
return NOERROR;  
}  
```  
  
 Antes de pasar un puntero hacia atrás por el método de interfaz dual, deberá convertir de MFC `IDispatch` puntero para el puntero de interfaz dual. Por ejemplo:  
  
```  
STDMETHODIMP CAutoClickDoc::XDualAClick::get_Position(
    IDualAutoClickPoint FAR* FAR* retval)  
{  
    METHOD_PROLOGUE(CAutoClickDoc,
    DualAClick)  
    LPDISPATCH lpDisp;  
    lpDisp = pThis->GetPosition();
lpDisp->QueryInterface(IID_IDualAutoClickPoint, (LPVOID*)retval);

    return NOERROR;  
}  
```  
  
## <a name="registering-the-applications-type-library"></a>Registrar la biblioteca de tipos de la aplicación  
 AppWizard no genera código para registrar la biblioteca de tipos de una aplicación de servidor de automatización OLE en el sistema. Aunque existen otras formas de registrar la biblioteca de tipos, es conveniente que la aplicación registrar la biblioteca de tipos cuando está actualizando su información de tipo OLE, es decir, cada vez que se ejecuta la aplicación independiente.  
  
 Para registrar la biblioteca de tipos de la aplicación cada vez que se ejecuta la aplicación actuar por sí sola:  
  
-   Incluir AFXCTL. H en el estándar incluye el archivo de encabezado STDAFX. H, para tener acceso a la definición de la `AfxOleRegisterTypeLib` (función).  
  
-   En la aplicación `InitInstance` funcionar, busque la llamada a `COleObjectFactory::UpdateRegistryAll`. Después de esta llamada, agregue una llamada a `AfxOleRegisterTypeLib`, especificando la **LIBID** correspondiente a la biblioteca de tipos, junto con el nombre de la biblioteca de tipos:  
  
 ''' * / / Cuando se inicia una aplicación de servidor independiente, es una buena idea * / / para actualizar el registro del sistema en caso de que se haya dañado.  
    m_server.UpdateRegistry(OAT_DISPATCH_OBJECT);

 COleObjectFactory::UpdateRegistryAll(); * / / DUAL_SUPPORT_START * / / asegurarse de que se ha registrado la biblioteca de tipos o interfaz dual no funcionará.  
AfxOleRegisterTypeLib(AfxGetInstanceHandle(), LIBID_ACDual, _T("AutoClik.TLB")); * / / DUAL_SUPPORT_END  
 ```  
  
## Modifying Project Build Settings to Accommodate Type Library Changes  
 To modify a project's build settings so that a header file containing **UUID** definitions is generated by MkTypLib whenever the type library is rebuilt:  
  
1.  On the **Build** menu, click **Settings**, and then select the ODL file from the file list for each configuration.  
  
2.  Click the **OLE Types** tab and specify a filename in the **Output header** filename field. Use a filename that is not already used by your project, because MkTypLib will overwrite any existing file. Click **OK** to close the **Build Settings** dialog box.  
  
 To add the **UUID** definitions from the MkTypLib-generated header file to your project:  
  
1.  Include the MkTypLib-generated header file in your standard includes header file, STDAFX.H.  
  
2.  Create a new file, INITIIDS.CPP, and add it to your project. In this file, include your MkTypLib-generated header file after including OLE2.H and INITGUID.H:  
  
 ```  
    initIIDs.c: define IID para interfaces duales  
    No debe compilarse con el encabezado precompilado.  
      #<a name="include-ole2h"></a>incluir < ole2.h >  
      #<a name="include-initguidh"></a>incluir < initguid.h >  
      #<a name="include-acdualh"></a>incluir "acdual.h"  
 ```  
  
3.  On the **Build** menu, click **Settings**, and then select INITIIDS.CPP from the file list for each configuration.  
  
4.  Click the **C++** tab, click category **Precompiled Headers**, and select the **Not using precompiled headers** radio button. Click OK to close the **Build Settings** dialog box.  
  
## Specifying the Correct Object Class Name in the Type Library  
 The wizards shipped with Visual C++ incorrectly use the implementation class name to specify the coclass in the server's ODL file for OLE-creatable classes. While this will work, the implementation class name is probably not the class name you want users of your object to use. To specify the correct name, open the ODL file, locate each coclass statement, and replace the implementation class name with the correct external name.  
  
 Note that when the coclass statement is changed, the variable names of **CLSID**s in the MkTypLib-generated header file will change accordingly. You will need to update your code to use the new variable names.  
  
## Handling Exceptions and the Automation Error Interfaces  
 Your automation object's methods and property accessor functions may throw exceptions. If so, you should handle them in your dual-interface implementation and pass information about the exception back to the controller through the OLE Automation error-handling interface, **IErrorInfo**. This interface provides for detailed, contextual error information through both `IDispatch` and VTBL interfaces. To indicate that an error handler is available, you should implement the **ISupportErrorInfo** interface.  
  
 To illustrate the error-handling mechanism, assume that the ClassWizard-generated functions used to implement the standard dispatch support throw exceptions. MFC's implementation of **IDispatch::Invoke** typically catches these exceptions and converts them into an EXCEPTINFO structure that is returned through the `Invoke` call. However, when VTBL interface is used, you are responsible for catching the exceptions yourself. As an example of protecting your dual-interface methods:  
  
```  
STDMETHODIMP CAutoClickDoc::XDualAClick::put_text(BSTR newText)  
{  
    METHOD_PROLOGUE (CAutoClickDoc, DualAClick)  
    TRY_DUAL(IID_IDualAClick) {* / / MFC se convierte automáticamente en Unicode BSTR a * / / Ansi CString, si es necesario...  
    pThis -> m_str = TextoNuevo;  
    devolver NOERROR;  
 }  
    CATCH_ALL_DUAL}  
```  
  
 `CATCH_ALL_DUAL` takes care of returning the correct error code when an exception occurs. `CATCH_ALL_DUAL` converts an MFC exception into OLE Automation error-handling information using the **ICreateErrorInfo** interface. (An example `CATCH_ALL_DUAL` macro is in the file MFCDUAL.H in the [ACDUAL](../visual-cpp-samples.md) sample. The function it calls to handle exceptions, `DualHandleException`, is in the file MFCDUAL.CPP.) `CATCH_ALL_DUAL` determines the error code to return based on the type of exception that occurred:  
  
- [COleDispatchException](../mfc/reference/coledispatchexception-class.md) - In this case, `HRESULT` is constructed using the following code:  
  
 ```  
    hr = MAKE_HRESULT(SEVERITY_ERROR,
    FACILITY_ITF,   
 (e -> m_wCode + 0 x 200));

 ```  
  
     This creates an `HRESULT` specific to the interface that caused the exception. The error code is offset by 0x200 to avoid any conflicts with system-defined `HRESULT`s for standard OLE interfaces.  
  
- [CMemoryException](../mfc/reference/cmemoryexception-class.md) - In this case, `E_OUTOFMEMORY` is returned.  
  
-   Any other exception - In this case, `E_UNEXPECTED` is returned.  
  
 To indicate that the OLE Automation error handler is used, you should also implement the **ISupportErrorInfo** interface.  
  
 First, add code to your automation class definition to show it supports **ISupportErrorInfo**.  
  
 Second, add code to your automation class's interface map to associate the **ISupportErrorInfo** implementation class with MFC's `QueryInterface` mechanism. The `INTERFACE_PART` statement matches the class defined for **ISupportErrorInfo**.  
  
 Finally, implement the class defined to support **ISupportErrorInfo**.  
  
 (The [ACDUAL](../visual-cpp-samples.md) sample contains three macros to help do these three steps, `DECLARE_DUAL_ERRORINFO`, `DUAL_ERRORINFO_PART`, and `IMPLEMENT_DUAL_ERRORINFO`, all contained in MFCDUAL.H.)  
  
 The following example implements a class defined to support **ISupportErrorInfo**. `CAutoClickDoc` is the name of your automation class and `IID_IDualAClick` is the **IID** for the interface that is the source of errors reported through the OLE Automation error object:  
  
```  
STDMETHODIMP_(ulong) CAutoClickDoc::XSupportErrorInfo::AddRef()   
{  
    METHOD_PROLOGUE (CAutoClickDoc, SupportErrorInfo)   
    valor devueltos pThis -> ExternalAddRef();

}   
STDMETHODIMP_(ulong) CAutoClickDoc::XSupportErrorInfo::Release()   
{   
    METHOD_PROLOGUE (CAutoClickDoc, SupportErrorInfo)   
    valor devueltos pThis -> ExternalRelease();

}   
STDMETHODIMP CAutoClickDoc::XSupportErrorInfo::QueryInterface (REFIID iid, LPVOID * ppvObj)   
{   
    METHOD_PROLOGUE (CAutoClickDoc, SupportErrorInfo)   
    valor devueltos pThis -> ExternalQueryInterface (& iid, ppvObj);

}   
STDMETHODIMP CAutoClickDoc::XSupportErrorInfo::InterfaceSupportsErrorInfo (REFIID iid)   
{   
    METHOD_PROLOGUE (CAutoClickDoc, SupportErrorInfo)   
    devolver (iid == IID_IDualAClick) S_OK: S_FALSE;   
}  
```  
  
## See Also  
 [Technical Notes by Number](../mfc/technical-notes-by-number.md)   
 [Technical Notes by Category](../mfc/technical-notes-by-category.md)

