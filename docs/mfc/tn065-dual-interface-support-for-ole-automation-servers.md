---
title: 'TN065: Compatibilidad con una interfaz Dual para los servidores de automatización OLE | Microsoft Docs'
ms.custom: ''
ms.date: 06/28/2018
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
ms.openlocfilehash: 5ef599c99cc46c2014ee2d72c538b55e59122848
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43209691"
---
# <a name="tn065-dual-interface-support-for-ole-automation-servers"></a>TN065: Compatibilidad con una interfaz dual para los servidores de Automation OLE

> [!NOTE]
> La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea. Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos. Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.

Esta nota describe cómo agregar compatibilidad con interfaz dual a una aplicación de servidor basada en MFC OLE Automation. El [ACDUAL](../visual-cpp-samples.md) ejemplo ilustra la compatibilidad con interfaz dual, y el código de ejemplo en esta nota procede de ACDUAL. Las macros que se describe en esta nota, como DECLARE_DUAL_ERRORINFO, DUAL_ERRORINFO_PART y IMPLEMENT_DUAL_ERRORINFO, forman parte del ejemplo ACDUAL y pueden encontrarse en MFCDUAL. H.

## <a name="dual-interfaces"></a>Interfaces duales

Aunque OLE Automation le permite implementar una `IDispatch` interfaz, una interfaz VTBL o una interfaz dual (que abarca ambas), Microsoft recomienda encarecidamente implementar interfaces duales para todos los objetos de automatización OLE de expuesto. Interfaces duales tienen ventajas considerables sobre `IDispatch`-únicas o VTBL interfaces:

- Enlace puede tener lugar en tiempo de compilación a través de la interfaz VTBL, o en tiempo de ejecución a través de `IDispatch`.

- Los controladores de automatización OLE que se pueden usar la interfaz VTBL pueden beneficiarse de mejorar el rendimiento.

- Los controladores de automatización OLE existentes que usan el `IDispatch` interfaz seguirán funcionando.

- La interfaz VTBL es más fácil llamar a desde C++.

- Interfaces duales son necesarias para la compatibilidad con características de soporte técnico del objeto Visual Basic.

## <a name="adding-dual-interface-support-to-a-ccmdtarget-based-class"></a>Agregar compatibilidad con interfaz Dual a una clase de CCmdTarget

Una interfaz dual es simplemente una interfaz personalizada que deriva de `IDispatch`. La manera más sencilla de implementar la compatibilidad con interfaz dual en una `CCmdTarget`-basado en clase consiste en implementar primero el envío normal de la interfaz en la clase mediante MFC y ClassWizard, a continuación, agregar la interfaz personalizada más adelante. En su mayor parte, la implementación de interfaz personalizado simplemente delegarán a MFC `IDispatch` implementación.

En primer lugar, modifique el archivo ODL de su servidor definir interfaces duales para los objetos. Para definir una interfaz dual, debe usar una instrucción de la interfaz, en lugar de la `DISPINTERFACE` instrucción que generan los asistentes de Visual C++. En lugar de quitar las existentes `DISPINTERFACE` instrucción, agregue una nueva instrucción de interfaz. Al conservar la `DISPINTERFACE` formulario, puede seguir usando ClassWizard para agregar propiedades y métodos al objeto, pero debe agregar los métodos y propiedades equivalentes a la instrucción de la interfaz.

Debe tener una declaración de interfaz de una interfaz dual el *OLEAUTOMATION* y *DUAL* atributos y la interfaz deben derivarse de `IDispatch`. Puede usar el [GUIDGEN](../visual-cpp-samples.md) ejemplo para crear un **IID** para la interfaz dual:

```IDL
[ uuid(0BDD0E81-0DD7-11cf-BBA8-444553540000), // IID_IDualAClick
    oleautomation,
    dual
]
interface IDualAClick : IDispatch
    {
    };
```

Una vez que la instrucción de la interfaz en su lugar, empezar a agregar entradas para los métodos y propiedades. Para interfaces duales, debe volver a organizar las listas de parámetros para que devuelven los métodos de las funciones de descriptor de acceso de propiedad en la interfaz dual un **HRESULT** y pasar sus valores devueltos como parámetros con los atributos `[retval,out]`. Recuerde que para las propiedades, necesitará agregar tanto de lectura (`propget`) y escritura (`propput`) tener acceso a la función con el mismo identificador. Por ejemplo:

```IDL
[propput, id(1)] HRESULT text([in] BSTR newText);
[propget, id(1)] HRESULT text([out, retval] BSTR* retval);
```

Después de que se definen los métodos y propiedades, deberá agregar una referencia a la instrucción de la interfaz en la instrucción de la coclase. Por ejemplo:

```IDL
[ uuid(4B115281-32F0-11cf-AC85-444553540000) ]
coclass Document
{
    dispinterface IAClick;
    [default] interface IDualAClick;
};
```

Una vez que se ha actualizado el archivo ODL, utilice el mecanismo de mapa de interfaz de MFC para definir una clase de implementación para la interfaz dual en la clase de objeto y crea las entradas correspondientes en de MFC `QueryInterface` mecanismo. Necesita una entrada en el `INTERFACE_PART` bloque para cada entrada de la instrucción de la interfaz de la ODL, además de las entradas para una interfaz de envío. Cada entrada ODL con el *propput* atributo tiene una función denominada `put_propertyname`. Cada entrada con el *propget* atributo tiene una función denominada `get_propertyname`.

Para definir una clase de implementación para la interfaz dual, agregue un `DUAL_INTERFACE_PART` bloque a la definición de clase de objeto. Por ejemplo:

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

Para conectar la interfaz dual para de MFC [QueryInterface](/windows/desktop/com/queryinterface--navigating-in-an-object) mecanismo, agregue un `INTERFACE_PART` entrada para el mapa de interfaz:

```cpp
BEGIN_INTERFACE_MAP(CAutoClickDoc, CDocument)
    INTERFACE_PART(CAutoClickDoc, DIID_IAClick, Dispatch)
    INTERFACE_PART(CAutoClickDoc, IID_IDualAClick, DualAClick)
END_INTERFACE_MAP()
```

A continuación, deberá rellenar la implementación de la interfaz. En su mayor parte, podrá delegar a MFC existente `IDispatch` implementación. Por ejemplo:

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

Para los métodos y funciones de descriptor de acceso de propiedad del objeto, deberá rellenar la implementación. Por lo general pueden delegar las funciones de método y propiedad a los métodos generados mediante el Asistente para clases. Sin embargo, si establece las propiedades para tener acceso a las variables directamente, deberá escribir el código para el valor de get/put a la variable. Por ejemplo:

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

## <a name="passing-dual-interface-pointers"></a>Pasar punteros de interfaz Dual

Pasar el puntero de interfaz dual no es sencillo, especialmente si necesita llamar a `CCmdTarget::FromIDispatch`. `FromIDispatch` solo funciona en de MFC `IDispatch` punteros. Es una manera de solucionar este problema para consultar el original `IDispatch` conjunto puntero hasta por MFC y pasar ese puntero a funciones que lo necesiten. Por ejemplo:

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

Antes de pasar un puntero hacia atrás por el método de interfaz dual, es posible que deba convertir de MFC `IDispatch` puntero en el puntero de interfaz dual. Por ejemplo:

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

AppWizard no genera código para registrar la biblioteca de tipos de una aplicación de servidor de automatización OLE en el sistema. Aunque hay otras formas de registrar la biblioteca de tipos, es conveniente tener la aplicación registrar la biblioteca de tipos cuando se está actualizando su información de tipo OLE, es decir, cada vez que se ejecuta la aplicación independiente.

Para registrar la biblioteca de tipos de la aplicación cada vez que se ejecuta la aplicación actuar por sí sola:

- Incluir AFXCTL. H en el estándar incluye el archivo de encabezado, STDAFX. H, para tener acceso a la definición de la `AfxOleRegisterTypeLib` función.

- En la aplicación `InitInstance` funcionar, busque la llamada a `COleObjectFactory::UpdateRegistryAll`. Después de esta llamada, agregue una llamada a `AfxOleRegisterTypeLib`, especificando el **LIBID** correspondiente a la biblioteca de tipos, junto con el nombre de la biblioteca de tipos:

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

## <a name="modifying-project-build-settings-to-accommodate-type-library-changes"></a>Modificar la configuración de compilación de proyecto para dar cabida a cambios de la biblioteca de tipos

Para modificar la configuración de compilación de un proyecto para que un archivo de encabezado que contiene **UUID** MkTypLib genera definiciones de cada vez que se vuelve a generar la biblioteca de tipos:

1. En el **compilar** menú, haga clic en **configuración**y, a continuación, seleccione el archivo ODL desde la lista de archivos para cada configuración.

2. Haga clic en el **OLE tipos** pestaña y especifique un nombre de archivo en el **encabezado de salida** campo de nombre de archivo. Use un nombre de archivo que no está usando ya en el proyecto, porque MkTypLib sobrescribirá cualquier archivo existente. Haga clic en **Aceptar** para cerrar el **configuración de compilación** cuadro de diálogo.

Para agregar la **UUID** definiciones desde el archivo de encabezado generado MkTypLib al proyecto:

1. Incluir MkTypLib generado por el archivo de encabezado en el estándar incluye el archivo de encabezado, STDAFX. H.

2. Cree un nuevo archivo, INITIIDS. CPP y agréguelo al proyecto. En este archivo, incluya el archivo de encabezado generado MkTypLib después de incluir OLE2. H y INITGUID. H:

    ```cpp
    // initIIDs.c: defines IIDs for dual interfaces
    // This must not be built with precompiled header.
    #include <ole2.h>
    #include <initguid.h>
    #include "acdual.h"
    ```

3. En el **compilar** menú, haga clic en **configuración**y, a continuación, seleccione INITIIDS. CPP de la lista de archivos para cada configuración.

4. Haga clic en el **C++** pestaña, haga clic en la categoría **encabezados precompilados**y seleccione el **no utilizar encabezados precompilados** botón de radio. Haga clic en Aceptar para cerrar el **configuración de compilación** cuadro de diálogo.

## <a name="specifying-the-correct-object-class-name-in-the-type-library"></a>Especifica el nombre de clase de objeto correcto en la biblioteca de tipos

Los asistentes que vienen con Visual C++ incorrectamente utilizan el nombre de clase de implementación para especificar la coclase en el archivo del servidor ODL para las clases que se pueden crear OLE. Aunque esto funcionará, el nombre de clase de implementación es probablemente no desea que los usuarios de su objeto de usar el nombre de clase. Para especificar el nombre correcto, abra el archivo ODL, busque cada instrucción de la coclase y reemplace el nombre de clase de implementación con el nombre externo correcto.

Tenga en cuenta que cuando se cambia la instrucción de la coclase, los nombres de variable de **CLSID**s en el archivo de encabezado generado MkTypLib cambiará en consecuencia. Deberá actualizar el código para usar los nuevos nombres de variable.

## <a name="handling-exceptions-and-the-automation-error-interfaces"></a>Administración de excepciones y las Interfaces de Error de automatización

Los métodos y funciones de descriptor de acceso de propiedad de su objeto de automatización pueden producir excepciones. Si por lo tanto, debe controlarlas en su implementación de interfaz dual y pasar información sobre la excepción vuelva al controlador mediante la interfaz de control de errores de automatización OLE, `IErrorInfo`. Esta interfaz proporciona información de error detallados y contextuales a través de ambos `IDispatch` e interfaces VTBL. Para indicar que está disponible un controlador de errores, debe implementar la `ISupportErrorInfo` interfaz.

Para ilustrar el mecanismo de control de errores, se supone que las funciones generadas ClassWizard usadas para implementar la compatibilidad con la distribución estándar producen excepciones. Implementación de MFC de `IDispatch::Invoke` normalmente detecta estas excepciones y los convierte en una estructura EXCEPTINFO que se devuelve a través de la `Invoke` llamar. Sin embargo, cuando se usa la interfaz VTBL, usted es responsable de detectar las excepciones usted mismo. Como ejemplo de la protección de los métodos de interfaz dual:

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

`CATCH_ALL_DUAL` se encarga de devolver el código de error correcto cuando se produce una excepción. `CATCH_ALL_DUAL` Convierte una excepción de MFC en la información de control de errores de OLE Automation mediante el `ICreateErrorInfo` interfaz. (Un ejemplo `CATCH_ALL_DUAL` macro se encuentra en el archivo MFCDUAL. H en el [ACDUAL](../visual-cpp-samples.md) ejemplo. La función llama para controlar las excepciones, `DualHandleException`, está en el archivo MFCDUAL. CPP.) `CATCH_ALL_DUAL` determina debe devolver en función del tipo de excepción que se produjo el código de error:

- [COleDispatchException](../mfc/reference/coledispatchexception-class.md) : en este caso, `HRESULT` se construye utilizando el código siguiente:

    ```cpp
    hr = MAKE_HRESULT(SEVERITY_ERROR, FACILITY_ITF, (e->m_wCode + 0x200));
    ```

     Esto crea un `HRESULT` específico de la interfaz que produjo la excepción. El código de error se desplaza por 0 x 200 para evitar conflictos con el definido por el sistema `HRESULT`s para interfaces OLE estándares.

- [CMemoryException](../mfc/reference/cmemoryexception-class.md) : en este caso, `E_OUTOFMEMORY` se devuelve.

- Cualquier otra excepción: en este caso, `E_UNEXPECTED` se devuelve.

Para indicar que se usa el controlador de errores de OLE Automation, también debe implementar la `ISupportErrorInfo` interfaz.

En primer lugar, agregue código a la definición de clase de automatización para mostrar es compatible con `ISupportErrorInfo`.

En segundo lugar, agregue código al mapa de interfaz de la clase de automatización para asociar el `ISupportErrorInfo` clase de implementación con de MFC `QueryInterface` mecanismo. El `INTERFACE_PART` instrucción coincide con la clase definida para `ISupportErrorInfo`.

Por último, implemente la clase definida para admitir `ISupportErrorInfo`.

(El [ACDUAL](../visual-cpp-samples.md) ejemplo contiene tres macros para ayudar a realizar estos tres pasos, `DECLARE_DUAL_ERRORINFO`, `DUAL_ERRORINFO_PART`, y `IMPLEMENT_DUAL_ERRORINFO`, todos los contenidos en MFCDUAL. H.)

En el ejemplo siguiente se implementa una clase definida para admitir `ISupportErrorInfo`. `CAutoClickDoc` es el nombre de la clase de automatización y `IID_IDualAClick` es el **IID** para la interfaz que es el origen de los errores notificados a través del objeto de error de OLE Automation:

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

[Notas técnicas por número](../mfc/technical-notes-by-number.md)  
[Notas técnicas por categoría](../mfc/technical-notes-by-category.md)  
