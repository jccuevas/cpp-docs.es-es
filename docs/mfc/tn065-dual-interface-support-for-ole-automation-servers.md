---
title: 'TN065: Compatibilidad con una interfaz dual para los servidores de automatización OLE'
ms.date: 06/28/2018
f1_keywords:
- vc.ole
helpviewer_keywords:
- dual interfaces [MFC], OLE Automation
- TN065 [MFC]
- ACDUAL sample [MFC]
- Automation servers [MFC], dual-interface support
ms.assetid: b5c8ed09-2f7f-483c-80fc-2a47ad896063
ms.openlocfilehash: 1508b5219f7bb7fd2e9c9a56c42c30bb99686804
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630391"
---
# <a name="tn065-dual-interface-support-for-ole-automation-servers"></a>TN065: Compatibilidad con una interfaz dual para los servidores de automatización OLE

> [!NOTE]
> La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea. Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos. Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.

En esta nota se describe cómo agregar compatibilidad con una interfaz dual a una aplicación de servidor de automatización OLE basada en MFC. El ejemplo [ACDUAL](../overview/visual-cpp-samples.md) muestra la compatibilidad con una interfaz dual y el código de ejemplo de esta nota se toma de ACDUAL. Las macros descritas en esta nota, como DECLARE_DUAL_ERRORINFO, DUAL_ERRORINFO_PART y IMPLEMENT_DUAL_ERRORINFO, forman parte del ejemplo ACDUAL y se pueden encontrar en del MFCDUAL. C.

## <a name="dual-interfaces"></a>Interfaces duales

Aunque la automatización OLE le permite implementar una `IDispatch` interfaz, una interfaz VTBL o una interfaz dual (que abarca ambos), Microsoft recomienda encarecidamente implementar interfaces duales para todos los objetos de automatización OLE expuestos. Las interfaces duales tienen ventajas `IDispatch`significativas solo con las interfaces de solo VTBL o de solo lectura:

- El enlace puede tener lugar en tiempo de compilación a través de la interfaz VTBL o en `IDispatch`tiempo de ejecución a través de.

- Los controladores de automatización OLE que pueden usar la interfaz VTBL pueden beneficiarse del rendimiento mejorado.

- Los controladores de OLE Automation existentes que `IDispatch` usan la interfaz seguirán funcionando.

- La interfaz VTBL es más fácil de llamar C++desde.

- Se requieren interfaces duales por compatibilidad con las características de compatibilidad con objetos Visual Basic.

## <a name="adding-dual-interface-support-to-a-ccmdtarget-based-class"></a>Agregar compatibilidad con una interfaz dual a una clase basada en CCmdTarget

Una interfaz dual es realmente simplemente una interfaz personalizada derivada de `IDispatch`. La manera más sencilla de implementar la compatibilidad con una interfaz dual `CCmdTarget`en una clase basada en es primero implementar la interfaz de envío normal en la clase mediante MFC y ClassWizard, y agregar la interfaz personalizada más adelante. En su mayor parte, la implementación de la interfaz personalizada simplemente devolverá a `IDispatch` la implementación de MFC.

En primer lugar, modifique el archivo ODL del servidor para definir interfaces duales para los objetos. Para definir una interfaz dual, debe usar una instrucción interface, en lugar de la `DISPINTERFACE` instrucción generada por los asistentes visuales. C++ En lugar de quitar la `DISPINTERFACE` instrucción existente, agregue una nueva instrucción interface. Conservando el `DISPINTERFACE` formulario, puede seguir usando ClassWizard para agregar propiedades y métodos al objeto, pero debe agregar las propiedades y los métodos equivalentes a la instrucción de interfaz.

Una instrucción interface para una interfaz dual debe tener los atributos *OLEAUTOMATION* y *dual* , y la interfaz debe derivarse de `IDispatch`. Puede usar el ejemplo de [GUIDGEN](../overview/visual-cpp-samples.md) para crear un **IID** para la interfaz dual:

```IDL
[ uuid(0BDD0E81-0DD7-11cf-BBA8-444553540000), // IID_IDualAClick
    oleautomation,
    dual
]
interface IDualAClick : IDispatch
    {
    };
```

Una vez que tenga la instrucción Interface en su lugar, comience a agregar entradas para los métodos y las propiedades. En el caso de interfaces duales, debe reorganizar las listas de parámetros para que los métodos y las funciones de descriptor de acceso de propiedades de la interfaz dual devuelvan `[retval,out]`un **valor HRESULT** y pasen los valores devueltos como parámetros con los atributos. Recuerde que, para las propiedades, necesitará agregar una función de acceso`propget`Read () y`propput`Write () con el mismo identificador. Por ejemplo: 

```IDL
[propput, id(1)] HRESULT text([in] BSTR newText);
[propget, id(1)] HRESULT text([out, retval] BSTR* retval);
```

Una vez definidos los métodos y las propiedades, debe agregar una referencia a la instrucción Interface en la instrucción coclass. Por ejemplo: 

```IDL
[ uuid(4B115281-32F0-11cf-AC85-444553540000) ]
coclass Document
{
    dispinterface IAClick;
    [default] interface IDualAClick;
};
```

Una vez actualizado el archivo ODL, use el mecanismo de mapa de interfaz de MFC para definir una clase de implementación para la interfaz dual en la clase de objeto y crear las entradas `QueryInterface` correspondientes en el mecanismo de MFC. Se necesita una entrada en el `INTERFACE_PART` bloque para cada entrada de la instrucción de interfaz del ODL, además de las entradas de una interfaz de envío. Cada entrada ODL con el atributo *PROPPUT* necesita una función denominada `put_propertyname`. Cada entrada con el atributo *propget* necesita una función denominada `get_propertyname`.

Para definir una clase de implementación para la interfaz dual, agregue `DUAL_INTERFACE_PART` un bloque a la definición de clase de objeto. Por ejemplo: 

```cpp
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

Para conectar la interfaz dual al mecanismo [QueryInterface](/windows/win32/com/queryinterface--navigating-in-an-object) de MFC, agregue una `INTERFACE_PART` entrada al mapa de interfaz:

```cpp
BEGIN_INTERFACE_MAP(CAutoClickDoc, CDocument)
    INTERFACE_PART(CAutoClickDoc, DIID_IAClick, Dispatch)
    INTERFACE_PART(CAutoClickDoc, IID_IDualAClick, DualAClick)
END_INTERFACE_MAP()
```

A continuación, debe rellenar la implementación de la interfaz. En su mayor parte, podrá delegar en la implementación de MFC `IDispatch` existente. Por ejemplo: 

```cpp
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
    REFIID iid,
    LPVOID* ppvObj)
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
    UINT itinfo,
    LCID lcid,
    ITypeInfo FAR* FAR* pptinfo)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    LPDISPATCH lpDispatch = pThis->GetIDispatch(FALSE);
    ASSERT(lpDispatch != NULL);

    return lpDispatch->GetTypeInfo(itinfo, lcid, pptinfo);
}

STDMETHODIMP CAutoClickDoc::XDualAClick::GetIDsOfNames(
    REFIID riid,
    OLECHAR FAR* FAR* rgszNames,
    UINT cNames,
    LCID lcid,
    DISPID FAR* rgdispid)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    LPDISPATCH lpDispatch = pThis->GetIDispatch(FALSE);
    ASSERT(lpDispatch != NULL);

    return lpDispatch->GetIDsOfNames(riid, rgszNames, cNames, lcid, rgdispid);
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
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    LPDISPATCH lpDispatch = pThis->GetIDispatch(FALSE);
    ASSERT(lpDispatch != NULL);

    return lpDispatch->Invoke(dispidMember, riid, lcid,
        wFlags, pdispparams, pvarResult, pexcepinfo, puArgErr);
}
```

En el caso de los métodos del objeto y las funciones de descriptor de acceso de propiedades, debe rellenar la implementación. Por lo general, las funciones de método y propiedad pueden delegar de nuevo a los métodos generados mediante ClassWizard. Sin embargo, si configura las propiedades para tener acceso directamente a las variables, debe escribir el código para obtener o colocar el valor en la variable. Por ejemplo: 

```cpp
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

## <a name="passing-dual-interface-pointers"></a>Pasar punteros de interfaz dual

Pasar el puntero de interfaz dual no es sencillo, especialmente si necesita llamar `CCmdTarget::FromIDispatch`a. `FromIDispatch`solo funciona en punteros `IDispatch` de MFC. Una manera de solucionar este fin es consultar el puntero original `IDispatch` configurado por MFC y pasar ese puntero a las funciones que lo necesiten. Por ejemplo: 

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

Antes de devolver un puntero a través del método de interfaz dual, puede que tenga que convertirlo del puntero `IDispatch` MFC al puntero de interfaz dual. Por ejemplo: 

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

## <a name="registering-the-applications-type-library"></a>Registrar la biblioteca de tipos de la aplicación

AppWizard no genera código para registrar una biblioteca de tipos de una aplicación de servidor de automatización OLE con el sistema. Aunque hay otras maneras de registrar la biblioteca de tipos, es conveniente que la aplicación registre la biblioteca de tipos cuando se está actualizando su información de tipo OLE, es decir, cada vez que la aplicación se ejecuta de forma independiente.

Para registrar la biblioteca de tipos de la aplicación cada vez que la aplicación se ejecuta de forma independiente:

- Incluir AFXCTL. H en el estándar incluye el archivo de encabezado, STDAFX. H, para tener acceso a la definición `AfxOleRegisterTypeLib` de la función.

- En la función de `InitInstance` la aplicación, busque la llamada `COleObjectFactory::UpdateRegistryAll`a. Después de esta llamada, agregue una llamada `AfxOleRegisterTypeLib`a, especificando el **identificador Libid** correspondiente a la biblioteca de tipos, junto con el nombre de la biblioteca de tipos:

    ```cpp
    // When a server application is launched stand-alone, it is a good idea
    // to update the system registry in case it has been damaged.
    m_server.UpdateRegistry(OAT_DISPATCH_OBJECT);

    COleObjectFactory::UpdateRegistryAll();

    // DUAL_SUPPORT_START
        // Make sure the type library is registered or dual interface won't work.
        AfxOleRegisterTypeLib(AfxGetInstanceHandle(),
            LIBID_ACDual,
            _T("AutoClik.TLB"));
    // DUAL_SUPPORT_END
    ```

## <a name="modifying-project-build-settings-to-accommodate-type-library-changes"></a>Modificar la configuración de compilación del proyecto para adaptarse a los cambios de la biblioteca de tipos

Modificar la configuración de compilación de un proyecto para que se genere un archivo de encabezado que contenga las definiciones de **UUID** cada vez que se vuelva a generar la biblioteca de tipos:

1. En el menú **compilar** , haga clic en **configuración**y, a continuación, seleccione el archivo ODL en la lista de archivos de cada configuración.

2. Haga clic en la pestaña **tipos OLE** y especifique un nombre de archivo en el campo Nombre de archivo del **encabezado de salida** . Use un nombre de archivo que no esté siendo usado por el proyecto, ya que MkTypLib sobrescribirá cualquier archivo existente. Haga clic en **Aceptar** para cerrar el cuadro de diálogo **configuración de compilación** .

Para agregar las definiciones de **UUID** del archivo de encabezado generado por MkTypLib al proyecto:

1. Incluya el archivo de encabezado generado por MkTypLib en el archivo de encabezado de inclusión estándar, *stdafx. h*.

2. Cree un nuevo archivo, INITIIDS. CPP y agréguelo al proyecto. En este archivo, incluya el archivo de encabezado generado por MkTypLib después de incluir OLE2. H y INITGUID. C

    ```cpp
    // initIIDs.c: defines IIDs for dual interfaces
    // This must not be built with precompiled header.
    #include <ole2.h>
    #include <initguid.h>
    #include "acdual.h"
    ```

3. En el menú **compilar** , haga clic en **configuración**y, a continuación, seleccione INITIIDS. CPP de la lista de archivos para cada configuración.

4. Haga clic **C++** en la pestaña, haga clic en **encabezados precompilados**de categoría y seleccione el botón de radio **no usar encabezados precompilados** . Haga clic en Aceptar para cerrar el cuadro de diálogo **configuración de compilación** .

## <a name="specifying-the-correct-object-class-name-in-the-type-library"></a>Especificar el nombre de clase de objeto correcto en la biblioteca de tipos

Los asistentes incluidos con Visual C++ incorrectamente usan el nombre de la clase de implementación para especificar la coclase en el archivo ODL del servidor para las clases que se pueden crear con OLE. Aunque esto funcionará, es probable que el nombre de la clase de implementación no sea el nombre de clase que desea que utilicen los usuarios de su objeto. Para especificar el nombre correcto, abra el archivo ODL, busque cada instrucción de coclase y reemplace el nombre de la clase de implementación por el nombre externo correcto.

Tenga en cuenta que cuando se cambia la instrucción de coclase, los nombres de variable de **CLSID**s en el archivo de encabezado generado por MkTypLib cambiarán en consecuencia. Tendrá que actualizar el código para utilizar los nuevos nombres de variable.

## <a name="handling-exceptions-and-the-automation-error-interfaces"></a>Controlar excepciones y las interfaces de error de automatización

Los métodos del objeto de automatización y las funciones de descriptor de acceso de propiedades pueden producir excepciones. Si es así, debe controlarlos en la implementación de interfaz dual y pasar información sobre la excepción al controlador a través de la interfaz de control de errores de automatización `IErrorInfo`OLE,. Esta interfaz proporciona información de error detallada `IDispatch` y contextual a través de las interfaces y VTBL. Para indicar que hay un controlador de errores disponible, debe implementar la `ISupportErrorInfo` interfaz.

Para ilustrar el mecanismo de control de errores, supongamos que las funciones generadas por ClassWizard utilizadas para implementar la compatibilidad con la distribución estándar producen excepciones. La implementación de MFC `IDispatch::Invoke` de normalmente detecta estas excepciones y las convierte en una estructura EXCEPTINFO que se devuelve a través de `Invoke` la llamada. Sin embargo, cuando se usa la interfaz VTBL, usted es responsable de detectar las excepciones usted mismo. Como ejemplo de protección de los métodos de interfaz dual:

```cpp
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

`CATCH_ALL_DUAL`se encarga de devolver el código de error correcto cuando se produce una excepción. `CATCH_ALL_DUAL`convierte una excepción de MFC en información de control de errores de automatización OLE `ICreateErrorInfo` mediante la interfaz. (Una macro `CATCH_ALL_DUAL` de ejemplo se encuentra en el archivo del mfcdual. H en el ejemplo [ACDUAL](../overview/visual-cpp-samples.md) . La función a la que llama para controlar `DualHandleException`las excepciones,, está en el archivo del mfcdual. CPP). `CATCH_ALL_DUAL` determina el código de error que se va a devolver en función del tipo de excepción que se produjo:

- [COleDispatchException](../mfc/reference/coledispatchexception-class.md) : en este caso, `HRESULT` se construye con el código siguiente:

    ```cpp
    hr = MAKE_HRESULT(SEVERITY_ERROR, FACILITY_ITF, (e->m_wCode + 0x200));
    ```

   Esto crea un `HRESULT` específico para la interfaz que produjo la excepción. El código de error está desplazado por 0x200 para evitar conflictos con las `HRESULT`interfaces de OLE estándar definidas por el sistema.

- [CMemoryException](../mfc/reference/cmemoryexception-class.md) : en este caso, `E_OUTOFMEMORY` se devuelve.

- Cualquier otra excepción, en este caso, `E_UNEXPECTED` se devuelve.

Para indicar que se utiliza el controlador de errores de automatización OLE, también debe implementar `ISupportErrorInfo` la interfaz.

En primer lugar, agregue código a la definición de clase de automatización `ISupportErrorInfo`para mostrarlo.

En segundo lugar, agregue código al mapa de interfaz de la clase de `ISupportErrorInfo` automatización para asociar la `QueryInterface` clase de implementación con el mecanismo de MFC. La `INTERFACE_PART` instrucción coincide con la clase definida `ISupportErrorInfo`para.

Por último, implemente la clase definida `ISupportErrorInfo`para admitir.

(El ejemplo [ACDUAL](../overview/visual-cpp-samples.md) contiene tres macros para ayudar a realizar estos tres `DECLARE_DUAL_ERRORINFO`pasos `DUAL_ERRORINFO_PART`,, `IMPLEMENT_DUAL_ERRORINFO`y, todos ellos contenidos en del mfcdual. H).

En el ejemplo siguiente se implementa una clase definida para `ISupportErrorInfo`admitir. `CAutoClickDoc`es el nombre de la clase de automatización `IID_IDualAClick` y es el **IID** de la interfaz que es el origen de los errores que se registran a través del objeto de error de automatización OLE:

```cpp
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
    REFIID iid,
    LPVOID* ppvObj)
{
    METHOD_PROLOGUE(CAutoClickDoc, SupportErrorInfo)
    return pThis->ExternalQueryInterface(&iid, ppvObj);
}

STDMETHODIMP CAutoClickDoc::XSupportErrorInfo::InterfaceSupportsErrorInfo(
    REFIID iid)
{
    METHOD_PROLOGUE(CAutoClickDoc, SupportErrorInfo)
    return (iid == IID_IDualAClick) S_OK : S_FALSE;
}
```

## <a name="see-also"></a>Vea también

[Notas técnicas por número](../mfc/technical-notes-by-number.md)<br/>
[Notas técnicas por categoría](../mfc/technical-notes-by-category.md)
