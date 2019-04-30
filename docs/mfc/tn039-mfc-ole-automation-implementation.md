---
title: 'TN039: Implementación de MFC / OLE Automation'
ms.date: 06/28/2018
f1_keywords:
- vc.mfc.ole
helpviewer_keywords:
- MFC, COM support
- IDispatch interface
- MFC, OLE DB and
- TN039
- Automation, MFC COM interface entry points
ms.assetid: 765fa3e9-dd54-4f08-9ad2-26e0546ff8b6
ms.openlocfilehash: cd6f8d681ef7e6517f2172ca6b22b13723a962fd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62305494"
---
# <a name="tn039-mfcole-automation-implementation"></a>TN039: Implementación de Automation MFC/OLE

> [!NOTE]
> La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea. Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos. Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.

## <a name="overview-of-ole-idispatch-interface"></a>Información general de la interfaz de IDispatch OLE

El `IDispatch` interfaz es el medio por el que las aplicaciones exponen métodos y propiedades de forma que otras aplicaciones, como Visual BASIC u otros lenguajes, pueden hacer uso de las características de la aplicación. La parte más importante de esta interfaz es la `IDispatch::Invoke` función. MFC utiliza "mapas de envío" para implementar `IDispatch::Invoke`. El mapa de envíos proporciona la información de implementación de MFC en el diseño o la "forma" de su `CCmdTarget`-las clases derivadas, que puede manipular las propiedades del objeto directamente o llamar a funciones dentro de su objeto para satisfacer miembro `IDispatch::Invoke` solicitudes.

En su mayor parte de ClassWizard y MFC cooperan para ocultar la mayoría de los detalles de automatización OLE desde el programador de aplicaciones. El programador se concentra en la funcionalidad real para exponer en la aplicación y no tiene que preocuparse por la estructura subyacente.

Hay casos, sin embargo, cuando sea necesario comprender lo que MFC está realizando en segundo plano. Esta nota abordará cómo asigna el marco de trabajo **DISPID**s a las funciones miembro y propiedades. Conocimiento del algoritmo de MFC utiliza para asignar **DISPID**s solo es necesario cuando necesite conocer los identificadores, como cuando se crea una biblioteca de tipos"" para los objetos de la aplicación.

## <a name="mfc-dispid-assignment"></a>Asignación de MFC DISPID

Aunque el usuario final de la automatización (usuario de Visual Basic, por ejemplo), ve los nombres reales de la automatización habilitada propiedades y métodos en su código (por ejemplo, obj. ShowWindow), la implementación de `IDispatch::Invoke` no recibe los nombres reales. Por motivos de optimización, recibe un **DISPID**, que es 32 bits "mágicas" que describe el método o propiedad que se tiene acceso. Estos **DISPID** valores se devuelven desde el `IDispatch` implementación a través de otro método, denominado `IDispatch::GetIDsOfNames`. Llamará a una aplicación de cliente de automatización `GetIDsOfNames` una vez por cada miembro o propiedad intenta obtener acceso y almacenar en caché para las llamadas posteriores a `IDispatch::Invoke`. De este modo, la búsqueda de cadenas costoso es sólo realiza una vez por el uso de objetos, en lugar de una vez por `IDispatch::Invoke` llamar.

MFC determina la **DISPID**para cada método y propiedad en función de dos cosas:

- La distancia desde la parte superior del mapa de envíos (1 relativo)

- La distancia del mapa de envíos de la clase más derivada (0 relativa)

El **DISPID** se divide en dos partes. El **LOWORD** de la **DISPID** contiene el primer componente, la distancia desde la parte superior del mapa de envíos. El **HIWORD** contiene la distancia desde la clase más derivada. Por ejemplo:

```cpp
class CDispPoint : public CCmdTarget
{
public:
    short m_x, m_y;
    // ...
    DECLARE_DISPATCH_MAP()
    // ...
};

class CDisp3DPoint : public CDispPoint
{
public:
    short m_z;
    // ...
    DECLARE_DISPATCH_MAP()
    // ...
};

BEGIN_DISPATCH_MAP(CDispPoint, CCmdTarget)
    DISP_PROPERTY(CDispPoint, "x", m_x, VT_I2)
    DISP_PROPERTY(CDispPoint, "y", m_y, VT_I2)
END_DISPATCH_MAP()

BEGIN_DISPATCH_MAP(CDisp3DPoint, CDispPoint)
    DISP_PROPERTY(CDisp3DPoint, "z", m_z, VT_I2)
END_DISPATCH_MAP()
```

Como puede ver, hay dos clases, que exponen interfaces de automatización OLE. Una de estas clases se deriva de la otra y, por tanto, aprovecha la funcionalidad de la clase base, incluido el elemento de automatización OLE ("x" e "y" propiedades en este caso).

MFC generará **DISPID**s para la clase CDispPoint como sigue:

```cpp
property X    (DISPID)0x00000001
property Y    (DISPID)0x00000002
```

Dado que las propiedades no están en una clase base, el **HIWORD** de la **DISPID** siempre es cero (la distancia desde la clase más derivada para CDispPoint es cero).

MFC generará **DISPID**s para la clase CDisp3DPoint como sigue:

```cpp
property Z    (DISPID)0x00000001
property X    (DISPID)0x00010001
property Y    (DISPID)0x00010002
```

La propiedad Z tiene un **DISPID** con un cero **HIWORD** puesto que se define en la clase que expone las propiedades, CDisp3DPoint. Puesto que las propiedades X e Y se definen en una clase base, el **HIWORD** de la **DISPID** es 1, ya que es la clase en que se definen estas propiedades a una distancia de una derivación de la clase más derivada.

> [!NOTE]
> El **LOWORD** siempre viene determinada por la posición en el mapa, incluso si existen entradas en la asignación explícita **DISPID** (vea la sección siguiente para obtener información sobre la **_ID** las versiones de la `DISP_PROPERTY` y `DISP_FUNCTION` macros).

## <a name="advanced-mfc-dispatch-map-features"></a>MFC envío mapa características avanzadas

Hay una serie de características adicionales que no es compatible con ClassWizard con esta versión de Visual C++. Admite ClassWizard `DISP_FUNCTION`, `DISP_PROPERTY`, y `DISP_PROPERTY_EX` que define un método, propiedad de variable de miembro y propiedad de función de miembro get/set, respectivamente. Estas capacidades suelen ser todo lo que es necesario para crear la mayoría de los servidores de automatización.

Se pueden usar las siguientes macros adicionales cuando las macros de ClassWizard compatibles no son adecuadas: `DISP_PROPERTY_NOTIFY`, y `DISP_PROPERTY_PARAM`.

## <a name="disppropertynotify--macro-description"></a>DISP_PROPERTY_NOTIFY: Descripción de la Macro

```cpp
DISP_PROPERTY_NOTIFY(
    theClass,
    pszName,
    memberName,
    pfnAfterSet,
    vtPropType)
```

### <a name="parameters"></a>Parámetros

*theClass*<br/>
Nombre de la clase.

*pszName*<br/>
Nombre externo de la propiedad.

*memberName*<br/>
Nombre de la variable de miembro en el que se almacena la propiedad.

*pfnAfterSet*<br/>
Nombre de función miembro debe llamar cuando se cambia la propiedad.

*vtPropType*<br/>
Valor que especifica el tipo de propiedad.

### <a name="remarks"></a>Comentarios

Esta macro es muy similar DISP_PROPERTY, salvo que acepte un argumento adicional. El argumento adicional, *pfnAfterSet,* debe ser una función miembro que no devuelve nada y no toma ningún parámetro, 'void OnPropertyNotify()'. Se llamará **después** se ha modificado la variable miembro.

## <a name="disppropertyparam--macro-description"></a>DISP_PROPERTY_PARAM: Descripción de la Macro

```cpp
DISP_PROPERTY_PARAM(
    theClass,
    pszName,
    pfnGet,
    pfnSet,
    vtPropType,
    vtsParams)
```

### <a name="parameters"></a>Parámetros

*theClass*<br/>
Nombre de la clase.

*pszName*<br/>
Nombre externo de la propiedad.

*memberGet*<br/>
Nombre de la función miembro que se usa para obtener la propiedad.

*memberSet*<br/>
Nombre de la función miembro que se usa para establecer la propiedad.

*vtPropType*<br/>
Valor que especifica el tipo de propiedad.

*vtsParams*<br/>
Una cadena de espacio separados VTS_ para cada parámetro.

### <a name="remarks"></a>Comentarios

Mucho como el DISP_PROPERTY_EX (macro), esta macro define una propiedad que se accede con funciones de miembro Get y Set independientes. Sin embargo, esta macro, permite especificar una lista de parámetros para la propiedad. Esto es útil para implementar propiedades indizadas o con parámetros de alguna otra manera. Los parámetros siempre se colocará en primer lugar, seguido por el nuevo valor para la propiedad. Por ejemplo:

```cpp
DISP_PROPERTY_PARAM(CMyObject, "item", GetItem, SetItem, VT_DISPATCH, VTS_I2 VTS_I2)
```

correspondería para obtener y establecer las funciones miembro:

```cpp
LPDISPATCH CMyObject::GetItem(short row, short col)
void CMyObject::SetItem(short row, short col, LPDISPATCH newValue)
```

## <a name="dispxxxxid--macro-descriptions"></a>DISP_XXXX_ID: Descripciones de macros

```cpp
DISP_FUNCTION_ID(
    theClass,
    pszName,
    dispid,
    pfnMember,
    vtRetVal,
    vtsParams)
DISP_PROPERTY_ID(
    theClass,
    pszName,
    dispid,
    memberName,
    vtPropType)
DISP_PROPERTY_NOTIFY_ID(
    theClass,
    pszName,
    dispid,
    memberName,
    pfnAfterSet,
    vtPropType)
DISP_PROPERTY_EX_ID(
    theClass,
    pszName,
    dispid,
    pfnGet,
    pfnSet,
    vtPropType)
DISP_PROPERTY_PARAM_ID(
    theClass,
    pszName,
    dispid,
    pfnGet,
    pfnSet,
    vtPropType,
    vtsParams)
```

### <a name="parameters"></a>Parámetros

*theClass*<br/>
Nombre de la clase.

*pszName*<br/>
Nombre externo de la propiedad.

*dispid*<br/>
El DISPID fijo para la propiedad o método.

*pfnGet*<br/>
Nombre de la función miembro que se usa para obtener la propiedad.

*pfnSet*<br/>
Nombre de la función miembro que se usa para establecer la propiedad.

*memberName*<br/>
El nombre de la variable miembro para asignar a la propiedad

*vtPropType*<br/>
Valor que especifica el tipo de propiedad.

*vtsParams*<br/>
Una cadena de espacio separados VTS_ para cada parámetro.

### <a name="remarks"></a>Comentarios

Estas macros le permiten especificar un **DISPID** en lugar de permitir MFC automáticamente asignar uno. Estas macros de avanzadas tienen los mismos nombres, salvo que el Id. se anexa al nombre de la macro (p. ej. **DISP_PROPERTY_ID**) y el identificador viene determinada por el parámetro que se especifican justo después del *pszName* parámetro. Consulte AFXDISP. H para obtener más información sobre estas macros. El **_ID** entradas deben colocarse al final del mapa de envíos. Afectará a automático **DISPID** generación en la misma manera que no **_ID** sería la versión de la macro (la **DISPID**s se determinan por posición). Por ejemplo:

```cpp
BEGIN_DISPATCH_MAP(CDisp3DPoint, CCmdTarget)
    DISP_PROPERTY(CDisp3DPoint, "y", m_y, VT_I2)
    DISP_PROPERTY(CDisp3DPoint, "z", m_z, VT_I2)
    DISP_PROPERTY_ID(CDisp3DPoint, "x", 0x00020003, m_x, VT_I2)
END_DISPATCH_MAP()
```

MFC generará envío (DISPID) para la clase CDisp3DPoint como sigue:

```cpp
property X    (DISPID)0x00020003
property Y    (DISPID)0x00000002
property Z    (DISPID)0x00000001
```

Especificar un fijo **DISPID** es útil para mantener la compatibilidad con versiones anteriores a una interfaz de envío existente previamente, o para implementar ciertas propiedades o métodos definidos por el sistema (normalmente está indicado por un valor negativo  **DISPID**, como el **DISPID_NEWENUM** colección).

## <a name="retrieving-the-idispatch-interface-for-a-coleclientitem"></a>Recuperación de la interfaz IDispatch para un COleClientItem

Muchos servidores será compatible con automatización dentro de sus objetos de documento, junto con la funcionalidad de servidor OLE. Para obtener acceso a esta interfaz de automatización, es necesario acceder directamente a la `COleClientItem::m_lpObject` variable miembro. El código siguiente recuperará el `IDispatch` para un objeto derivado de la interfaz `COleClientItem`. Puede incluir el código siguiente en la aplicación si encuentra esta funcionalidad es necesario:

```cpp
LPDISPATCH CMyClientItem::GetIDispatch()
{
    ASSERT_VALID(this);
    ASSERT(m_lpObject != NULL);

    LPUNKNOWN lpUnk = m_lpObject;

    Run();      // must be running

    LPOLELINK lpOleLink = NULL;
    if (m_lpObject->QueryInterface(IID_IOleLink,
        (LPVOID FAR*)&lpOleLink) == NOERROR)
    {
        ASSERT(lpOleLink != NULL);
        lpUnk = NULL;
        if (lpOleLink->GetBoundSource(&lpUnk) != NOERROR)
        {
            TRACE0("Warning: Link is not connected!\n");
            lpOleLink->Release();
            return NULL;
        }
        ASSERT(lpUnk != NULL);
    }

    LPDISPATCH lpDispatch = NULL;
    if (lpUnk->QueryInterface(IID_IDispatch, &lpDispatch) != NOERROR)
    {
        TRACE0("Warning: does not support IDispatch!\n");
        return NULL;
    }

    ASSERT(lpDispatch != NULL);
    return lpDispatch;
}
```

Devuelve la interfaz de envío de esta función, a continuación, se podría utilizada directamente o conectada a un `COleDispatchDriver` para el acceso de seguridad de tipos. Si desea usarla directamente, asegúrese de que se llama a su `Release` miembro cuando a través con el puntero (el `COleDispatchDriver` destructor hace esto de forma predeterminada).

## <a name="see-also"></a>Vea también

[Notas técnicas por número](../mfc/technical-notes-by-number.md)<br/>
[Notas técnicas por categoría](../mfc/technical-notes-by-category.md)
