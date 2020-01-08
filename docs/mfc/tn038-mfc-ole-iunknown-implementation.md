---
title: 'TN038: implementación de IUnknown en MFC-OLE'
ms.date: 06/28/2018
helpviewer_keywords:
- aggregation macros [MFC]
- COM interfaces, base interface
- IUnknown interface
- END_INTERFACE_MAP macro [MFC]
- TN038
- BEGIN_INTERFACE_PART macro [MFC]
- DECLARE_INTERFACE_MAP macro [MFC]
- BEGIN_INTERFACE_MAP macro [MFC]
- OLE [MFC], implementing IUnknown interface
- METHOD_PROLOGUE macro [MFC]
- STDMETHOD macro [MFC]
- END_INTERFACE_PART macro [MFC]
- INTERFACE_PART macro
ms.assetid: 19d946ba-beaf-4881-85c6-0b598d7f6f11
ms.openlocfilehash: 9ceb903ec38bc0ad7cfdee1c59babd2379422ac3
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302359"
---
# <a name="tn038-mfcole-iunknown-implementation"></a>TN038: Implementación de IUnknown en MFC/OLE

> [!NOTE]
> La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea. Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos. Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.

En el corazón de OLE 2 se encuentra el “Modelo de objetos componentes de OLE”, también conocido como COM. COM define un estándar sobre cómo se comunican entre sí los objetos al cooperar. Esto incluye los detalles relativos al aspecto que tiene un “objeto”, incluido el modo en que se envían los métodos en un objeto. COM también define una clase base de la que se derivan todas las clases compatibles con COM. Esta clase base es [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown). Aunque la interfaz [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) se conoce como una C++ clase, com no es específico de ningún lenguaje: se puede implementar en C, Pascal o cualquier otro lenguaje que admita el diseño binario de un objeto com.

OLE hace referencia a todas las clases derivadas de [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) como "interfaces". Se trata de una distinción importante, ya que una "interfaz" como [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) no conlleva ninguna implementación. Simplemente define el protocolo por el que se comunican los objetos, no lo que hacen específicamente esas implementaciones. Esto es razonable para un sistema que permite la máxima flexibilidad. Es responsabilidad de MFC implementar un comportamiento predeterminado para programas escritos en MFC o C++.

Para entender la implementación de MFC de [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) , primero debe comprender cuál es la interfaz. A continuación se define una versión simplificada de [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) :

```cpp
class IUnknown
{
public:
    virtual HRESULT QueryInterface(REFIID iid, void** ppvObj) = 0;
    virtual ULONG AddRef() = 0;
    virtual ULONG Release() = 0;
};
```

> [!NOTE]
> Ciertos detalles necesarios de convención de llamada, como `__stdcall`, se dejan fuera de esta ilustración.

Las funciones miembro [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref) y [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release) controlan la administración de memoria del objeto. COM usa un esquema de recuento de referencias para realizar un seguimiento de los objetos. Nunca se hace referencia a un objeto directamente, como se hace en C++. En su lugar, siempre se hace referencia a los objetos COM a través de un puntero. Para liberar el objeto cuando el propietario ha terminado de usarlo, se llama al miembro [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release) del objeto (en lugar de usar el operador Delete, como se haría para un objeto C++ tradicional). El mecanismo de recuento de referencias permite administrar varias referencias a un único objeto. Una implementación de [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref) y [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release) mantiene un recuento de referencias en el objeto: el objeto no se elimina hasta que su recuento de referencias llega a cero.

[AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref) y [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release) son bastante sencillos desde el punto de vista de la implementación. A continuación se muestra una implementación trivial:

```cpp
ULONG CMyObj::AddRef()
{
    return ++m_dwRef;
}

ULONG CMyObj::Release()
{
    if (--m_dwRef == 0)
    {
        delete this;
        return 0;
    }
    return m_dwRef;
}
```

La función miembro [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) es un poco más interesante. No es muy interesante tener un objeto cuyas únicas funciones miembro son [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref) y [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release) ; sería estupendo indicar al objeto que haga más cosas que las proporcionadas por [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) . Aquí es donde [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) es útil. Permite obtener una “interfaz” diferente en el mismo objeto. Estas interfaces se derivan normalmente de [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) y agregan funcionalidad adicional agregando nuevas funciones miembro. Las interfaces COM nunca tienen variables miembro declaradas en la interfaz y todas las funciones miembro se declaran como virtuales puras. Por ejemplo,

```cpp
class IPrintInterface : public IUnknown
{
public:
    virtual void PrintObject() = 0;
};
```

Para obtener un IPrintInterface si solo tiene un [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown), llame a [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) mediante el `IID` del `IPrintInterface`. Un `IID` es un número de 128 bits que identifica la interfaz de forma única. Hay un `IID` para cada interfaz que defina usted u OLE. Si *pUnk* es un puntero a un objeto [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) , el código para recuperar un IPrintInterface de este podría ser:

```cpp
IPrintInterface* pPrint = NULL;
if (pUnk->QueryInterface(IID_IPrintInterface, (void**)&pPrint) == NOERROR)
{
    pPrint->PrintObject();
    pPrint->Release();
    // release pointer obtained via QueryInterface
}
```

Parece bastante sencillo, pero ¿cómo se implementa un objeto que admita la interfaz IPrintInterface e [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) en este caso es sencillo, ya que IPrintInterface se deriva directamente de [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) — implementando IPrintInterface, [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) se admite automáticamente. Por ejemplo:

```cpp
class CPrintObj : public CPrintInterface
{
    virtual HRESULT QueryInterface(REFIID iid, void** ppvObj);
    virtual ULONG AddRef();
    virtual ULONG Release();
    virtual void PrintObject();
};
```

Las implementaciones de [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref) y [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release) serían exactamente iguales que las implementadas anteriormente. `CPrintObj::QueryInterface` tendría un aspecto similar al siguiente:

```cpp
HRESULT CPrintObj::QueryInterface(REFIID iid, void FAR* FAR* ppvObj)
{
    if (iid == IID_IUnknown || iid == IID_IPrintInterface)
    {
        *ppvObj = this;
        AddRef();
        return NOERROR;
    }
    return E_NOINTERFACE;
}
```

Como puede ver, si se reconoce el identificador de interfaz (IID), se devuelve un puntero al objeto; de lo contrario, se produce un error. Tenga en cuenta también que una [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) correcta genera una [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)implícita. Por supuesto, también debe implementar CEditObj::Print. Esto es sencillo porque IPrintInterface se derivó directamente de la interfaz [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) . Sin embargo, si desea admitir dos interfaces diferentes, ambas derivadas de [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown), tenga en cuenta lo siguiente:

```cpp
class IEditInterface : public IUnkown
{
public:
    virtual void EditObject() = 0;
};
```

Aunque hay diferentes maneras de implementar una clase compatible con IEditInterface e IPrintInterface —por ejemplo, usar la herencia múltiple de C++—, aquí nos centraremos en el uso de las clases anidadas para implementar esta funcionalidad.

```cpp
class CEditPrintObj
{
public:
    CEditPrintObj();

    HRESULT QueryInterface(REFIID iid, void**);
    ULONG AddRef();
    ULONG Release();
    DWORD m_dwRef;

    class CPrintObj : public IPrintInterface
    {
    public:
        CEditPrintObj* m_pParent;
        virtual HRESULT QueryInterface(REFIID iid, void** ppvObj);
        virtual ULONG AddRef();
        virtual ULONG Release();
    } m_printObj;

    class CEditObj : public IEditInterface
    {
    public:
        CEditPrintObj* m_pParent;
        virtual ULONG QueryInterface(REFIID iid, void** ppvObj);
        virtual ULONG AddRef();
        virtual ULONG Release();
    } m_editObj;
};
```

A continuación se incluye la implementación al completo:

```cpp
CEditPrintObj::CEditPrintObj()
{
    m_editObj.m_pParent = this;
    m_printObj.m_pParent = this;
}

ULONG CEditPrintObj::AddRef()
{
    return ++m_dwRef;
}

CEditPrintObj::Release()
{
    if (--m_dwRef == 0)
    {
        delete this;
        return 0;
    }
    return m_dwRef;
}

HRESULT CEditPrintObj::QueryInterface(REFIID iid, void** ppvObj)
{
    if (iid == IID_IUnknown || iid == IID_IPrintInterface)
    {
        *ppvObj = &m_printObj;
        AddRef();
        return NOERROR;
    }
    else if (iid == IID_IEditInterface)
    {
        *ppvObj = &m_editObj;
        AddRef();
        return NOERROR;
    }
    return E_NOINTERFACE;
}

ULONG CEditPrintObj::CEditObj::AddRef()
{
    return m_pParent->AddRef();
}

ULONG CEditPrintObj::CEditObj::Release()
{
    return m_pParent->Release();
}

HRESULT CEditPrintObj::CEditObj::QueryInterface(REFIID iid, void** ppvObj)
{
    return m_pParent->QueryInterface(iid, ppvObj);
}

ULONG CEditPrintObj::CPrintObj::AddRef()
{
    return m_pParent->AddRef();
}

ULONG CEditPrintObj::CPrintObj::Release()
{
    return m_pParent->Release();
}

HRESULT CEditPrintObj::CPrintObj::QueryInterface(REFIID iid, void** ppvObj)
{
    return m_pParent->QueryInterface(iid, ppvObj);
}
```

Observe que la mayor parte de la implementación de [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) se coloca en la clase CEditPrintObj en lugar de duplicar el código en CEditPrintObj:: CEditObj y CEditPrintObj:: CPrintObj. Esto reduce la cantidad de código y evita errores. El punto clave aquí es que, desde la interfaz IUnknown, es posible llamar a [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) para recuperar cualquier interfaz que el objeto pueda admitir y, desde cada una de esas interfaces, es posible hacer lo mismo. Esto significa que todas las funciones [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) disponibles en cada interfaz deben comportarse exactamente de la misma manera. Para que estos objetos incrustados llamen a la implementación en el “objeto externo”, se usa un puntero (m_pParent). Se inicializa el puntero m_pParent durante el constructor CEditPrintObj. A continuación, debería implementar también CEditPrintObj::CPrintObj::PrintObject y CEditPrintObj::CEditObj::EditObject. Se agregó un poco de código para agregar una característica: la capacidad de editar el objeto. Afortunadamente, es bastante raro que las interfaces tengan solo una función miembro (aunque puede pasar) y, en este caso, lo normal sería que EditObject y PrintObject se combinasen en una única interfaz.

Esto requeriría una explicación muy larga y una gran cantidad de código para un escenario tan simple. Las clases de MFC/OLE proporcionan una alternativa más sencilla. La implementación de MFC usa una técnica similar a la forma en que los mensajes de Windows se ajustan con Mapas de mensajes. Esta característica se denomina *mapas de interfaz* y se describe en la sección siguiente.

## <a name="mfc-interface-maps"></a>Mapas de interfaz de MFC

MFC/OLE incluye una implementación de “Mapas de interfaz” similar a los “Mapas de mensajes” y “Mapas de envío” de MFC en cuanto a su concepto y ejecución. Las características principales de Mapas de interfaz de MFC son las siguientes:

- Implementación estándar de [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown), integrada en la clase `CCmdTarget`.

- Mantenimiento del recuento de referencias, modificado por [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref) y [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)

- Implementación controlada por datos de [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q))

Además, los mapas de interfaz son compatibles con las siguientes características avanzadas:

- Compatibilidad con la creación de objetos COM agregables

- Compatibilidad con el uso de objetos agregados en la implementación de un objeto COM

- La implementación se puede enlazar y extender

Para obtener más información sobre la agregación, vea el tema de [agregación](/windows/win32/com/aggregation) .

La compatibilidad con el mapa de interfaz de MFC se basa en la clase `CCmdTarget`. `CCmdTarget` recuento de referencias "*tiene-a*", así como todas las funciones miembro asociadas a la implementación de [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) (el recuento de referencias, por ejemplo, está en `CCmdTarget`). Para crear una clase compatible con OLE y COM, derive una clase de `CCmdTarget` y use varias macros, así como funciones miembro de `CCmdTarget` para implementar las interfaces deseadas. La implementación de MFC usa clases anidadas para definir cada implementación de interfaz de manera muy similar al ejemplo anterior. Esto se facilita mediante una implementación estándar de IUnknown y mediante varias macros que eliminan parte del código repetitivo.

## <a name="interface-map-basics"></a>Conceptos básicos de mapa de interfaz

### <a name="to-implement-a-class-using-mfcs-interface-maps"></a>Para implementar una clase mediante los mapas de interfaz de MFC

1. Derive una clase directa o indirectamente de `CCmdTarget`.

2. Use la función `DECLARE_INTERFACE_MAP` en la definición de la clase derivada.

3. Para cada interfaz que desee admitir, use las macros BEGIN_INTERFACE_PART y END_INTERFACE_PART en la definición de clase.

4. En el archivo de implementación, use las macros BEGIN_INTERFACE_MAP y END_INTERFACE_MAP para definir el mapa de interfaz de la clase.

5. Para cada IID compatible, use la macro INTERFACE_PART entre las macros BEGIN_INTERFACE_MAP y END_INTERFACE_MAP para asignar ese IID a una "parte" específica de la clase.

6. Implemente cada una de las clases anidadas que representan las interfaces con las que se ofrece compatibilidad.

7. Utilice la macro METHOD_PROLOGUE para tener acceso al objeto primario derivado de `CCmdTarget`.

8. [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref), [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)y [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) pueden delegar en la `CCmdTarget` implementación de estas funciones (`ExternalAddRef`, `ExternalRelease`y `ExternalQueryInterface`).

El ejemplo CPrintEditObj expuesto anteriormente podría implementarse de la siguiente manera:

```cpp
class CPrintEditObj : public CCmdTarget
{
public:
    // member data and member functions for CPrintEditObj go here

// Interface Maps
protected:
    DECLARE_INTERFACE_MAP()

    BEGIN_INTERFACE_PART(EditObj, IEditInterface)
        STDMETHOD_(void, EditObject)();
    END_INTERFACE_PART(EditObj)

    BEGIN_INTERFACE_PART(PrintObj, IPrintInterface)
        STDMETHOD_(void, PrintObject)();
    END_INTERFACE_PART(PrintObj)
};
```

La declaración anterior crea una clase derivada de `CCmdTarget`. La macro DECLARE_INTERFACE_MAP indica al marco de trabajo que esta clase tendrá un mapa de interfaz personalizado. Además, las macros BEGIN_INTERFACE_PART y END_INTERFACE_PART definen clases anidadas, en este caso con los nombres CEditObj y CPrintObj (la X se usa solo para diferenciar las clases anidadas de las clases globales que empiezan por "C" y las clases de interfaz que Empiece por "I"). Se crean dos miembros anidados de estas clases: m_CEditObj y m_CPrintObj, respectivamente. Las macros declaran automáticamente las funciones [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref), [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)y [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) . por lo tanto, solo se declaran las funciones específicas de esta interfaz: EditObject y PrintObject (la macro OLE STDMETHOD se usa para que **_stdcall** y las palabras clave virtuales se proporcionen según corresponda para la plataforma de destino).

Para implementar el mapa de interfaz para esta clase:

```cpp
BEGIN_INTERFACE_MAP(CPrintEditObj, CCmdTarget)
    INTERFACE_PART(CPrintEditObj, IID_IPrintInterface, PrintObj)
    INTERFACE_PART(CPrintEditObj, IID_IEditInterface, EditObj)
END_INTERFACE_MAP()
```

Esto conectará el IID IID_IPrintInterface con m_CPrintObj e IID_IEditInterface con m_CEditObj respectivamente. La implementación de `CCmdTarget` de [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) (`CCmdTarget::ExternalQueryInterface`) utiliza este mapa para devolver punteros a m_CPrintObj y m_CEditObj cuando se solicitan. No es necesario incluir una entrada para `IID_IUnknown`; el marco de trabajo usará la primera interfaz del mapa (en este caso, m_CPrintObj) cuando `IID_IUnknown` se solicita.

Aunque la macro de BEGIN_INTERFACE_PART declare automáticamente las funciones [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref), [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release) y [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) , todavía tiene que implementarlas:

```cpp
ULONG FAR EXPORT CEditPrintObj::XEditObj::AddRef()
{
    METHOD_PROLOGUE(CEditPrintObj, EditObj)
    return pThis->ExternalAddRef();
}

ULONG FAR EXPORT CEditPrintObj::XEditObj::Release()
{
    METHOD_PROLOGUE(CEditPrintObj, EditObj)
    return pThis->ExternalRelease();
}

HRESULT FAR EXPORT CEditPrintObj::XEditObj::QueryInterface(
    REFIID iid,
    void FAR* FAR* ppvObj)
{
    METHOD_PROLOGUE(CEditPrintObj, EditObj)
    return (HRESULT)pThis->ExternalQueryInterface(&iid, ppvObj);
}

void FAR EXPORT CEditPrintObj::XEditObj::EditObject()
{
    METHOD_PROLOGUE(CEditPrintObj, EditObj)
    // code to "Edit" the object, whatever that means...
}
```

La implementación de CEditPrintObj::CPrintObj sería similar a las definiciones anteriores de CEditPrintObj::CEditObj. Aunque sería posible crear una macro que pudiese generar automáticamente estas funciones (este era el caso en etapas anteriores del desarrollo de MFC/OLE), resulta difícil establecer puntos de interrupción cuando una macro genera más de una línea de código. Por este motivo, este código se expande manualmente.

Mediante el uso de la implementación del marco de trabajo de mapas de mensajes, no se tuvieron que realizar varias cosas:

- Implementar QueryInterface

- Implementar AddRef y Release

- Declarar cualquiera de estos métodos integrados en ambas interfaces

Además el marco de trabajo usa mapas de mensajes internamente. Esto le permite derivar una clase de marco de trabajo, como, por ejemplo, `COleServerDoc`, que ya es compatible con determinadas interfaces y proporciona reemplazos o adiciones a las interfaces proporcionadas por el marco de trabajo. Puede hacerlo porque el marco de trabajo es totalmente compatible con la herencia de un mapa de interfaz a partir de una clase base. Este es el motivo por el que BEGIN_INTERFACE_MAP toma como segundo parámetro el nombre de la clase base.

> [!NOTE]
> Por lo general, no es posible reutilizar las implementaciones integradas de las interfaces OLE simplemente heredando la especialización incrustada de esa interfaz a partir de la versión MFC. Esto no es posible porque el uso de la macro METHOD_PROLOGUE para obtener acceso al objeto que contiene `CCmdTarget`derivado implica un *desplazamiento fijo* del objeto incrustado desde el objeto derivado de `CCmdTarget`. Esto significa, por ejemplo, que no puede derivar un XMyAdviseSink incrustado de la implementación de MFC en `COleClientItem::XAdviseSink`, porque XAdviseSink se basa en estar a un desplazamiento específico de la parte superior del objeto `COleClientItem`.

> [!NOTE]
> Sin embargo, puede delegar en la implementación de MFC para todas las funciones que desee que tengan el comportamiento predeterminado de MFC. Esto se hace en la implementación de MFC de `IOleInPlaceFrame` (XOleInPlaceFrame) en la clase `COleFrameHook` (delega en m_xOleInPlaceUIWindow para muchas funciones). Este diseño se ha elegido para reducir el tamaño en tiempo de ejecución de objetos que implementan muchas interfaces; elimina la necesidad de un puntero (tal como se usaba m_pParent en la sección anterior).

### <a name="aggregation-and-interface-maps"></a>Agregación y mapas de interfaz

Además de ser compatible con objetos COM independientes, MFC también es compatible con la agregación. La agregación es un tema demasiado complejo que se trata aquí. Consulte el tema de [agregación](/windows/win32/com/aggregation) para obtener más información sobre la agregación. Esta nota solo describe la compatibilidad con la agregación que se encuentra integrada en el marco de trabajo y los mapas de interfaz.

Hay dos maneras de utilizar la agregación: (1) usando un objeto COM compatible con la agregación e (2) implementando un objeto que pueda ser agregado por otro objeto. Estas capacidades se pueden denominar como “usar un objeto agregado” y “hacer que un objeto sea agregable”. MFC es compatible con ambas capacidades.

### <a name="using-an-aggregate-object"></a>Usar un objeto agregado

Para usar un objeto agregado, debe haber alguna manera de asociar el agregado en el mecanismo de QueryInterface. En otras palabras, el objeto agregado debe comportarse como si fuera una parte nativa del objeto. Así pues, el modo en que se asocia al mecanismo de mapa de interfaz de MFC, además de a la macro INTERFACE_PART, donde un objeto anidado se asigna a un IID, también puede declarar un objeto agregado como parte de la `CCmdTarget` clase derivada. Para ello, se usa la macro INTERFACE_AGGREGATE. Esto le permite especificar una variable miembro (que debe ser un puntero a una clase [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) o derivada), que se integrará en el mecanismo de mapa de interfaz. Si el puntero no es NULL cuando se llama a `CCmdTarget::ExternalQueryInterface`, el marco de trabajo llamará automáticamente a la función miembro [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) del objeto agregado, si el `IID` solicitado no es ninguno de los `IID`nativos admitidos por el propio objeto `CCmdTarget`.

#### <a name="to-use-the-interface_aggregate-macro"></a>Para usar la macro INTERFACE_AGGREGATE

1. Declare una variable miembro (una `IUnknown*`) que contenga un puntero al objeto agregado.

2. Incluya una macro INTERFACE_AGGREGATE en el mapa de interfaz, que hace referencia a la variable miembro por nombre.

3. En algún momento (normalmente durante `CCmdTarget::OnCreateAggregates`), inicialice la variable miembro en un valor que no sea NULL.

Por ejemplo:

```cpp
class CAggrExample : public CCmdTarget
{
public:
    CAggrExample();

protected:
    LPUNKNOWN m_lpAggrInner;
    virtual BOOL OnCreateAggregates();

    DECLARE_INTERFACE_MAP()
    // "native" interface part macros may be used here
};

CAggrExample::CAggrExample()
{
    m_lpAggrInner = NULL;
}

BOOL CAggrExample::OnCreateAggregates()
{
    // wire up aggregate with correct controlling unknown
    m_lpAggrInner = CoCreateInstance(CLSID_Example,
        GetControllingUnknown(), CLSCTX_INPROC_SERVER,
        IID_IUnknown, (LPVOID*)&m_lpAggrInner);

    if (m_lpAggrInner == NULL)
        return FALSE;
    // optionally, create other aggregate objects here
    return TRUE;
}

BEGIN_INTERFACE_MAP(CAggrExample, CCmdTarget)
    // native "INTERFACE_PART" entries go here
    INTERFACE_AGGREGATE(CAggrExample, m_lpAggrInner)
END_INTERFACE_MAP()
```

La variable m_lpAggrInner se inicializa en el constructor con un valor NULL. El marco de trabajo omite una variable miembro NULL en la implementación predeterminada de [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)). `OnCreateAggregates` es un buen lugar para crear realmente los objetos agregados. Tendrá que llamarlo explícitamente si va a crear el objeto fuera de la implementación de MFC de `COleObjectFactory`. La razón para crear agregados en `CCmdTarget::OnCreateAggregates`, así como el uso de `CCmdTarget::GetControllingUnknown`, serán evidentes al crear objetos agregables.

Esta técnica le dará su objeto de todas las interfaces compatibles con el objeto agregado además de sus interfaces nativas. Si solo quiere un subconjunto de las interfaces compatibles con el agregado, puede invalidar `CCmdTarget::GetInterfaceHook`. Esto permite un enlace de nivel muy bajo, similar a [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)). Lo normal es querer todas las interfaces que sean compatibles con el agregado.

### <a name="making-an-object-implementation-aggregatable"></a>Convertir en agregable una implementación de objeto

Para que un objeto sea agregable, la implementación de [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref), [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)y [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) debe delegar en un "control Unknown". En otras palabras, para que forme parte del objeto, debe delegar [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref), [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)y [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) en un objeto diferente, también derivado de [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown). Este “desconocido de control” se proporciona al objeto cuando se crea, es decir, se proporciona a la implementación de `COleObjectFactory`. Esta implementación implica una pequeña cantidad de sobrecarga y en algunos casos no es deseable, por lo que MFC hace que sea opcional. Para hacer que un objeto sea agregable, se debe llamar a `CCmdTarget::EnableAggregation` desde el constructor del objeto.

Si el objeto también utiliza agregados, asegúrese de pasar el “desconocido de control” correcto a los objetos agregados. Normalmente, este puntero [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) se pasa al objeto cuando se crea el agregado. Por ejemplo, el parámetro pUnkOuter es el “desconocido de control” para los objetos creados con `CoCreateInstance`. El puntero correcto “desconocido de control” se puede recuperar llamando a `CCmdTarget::GetControllingUnknown`. Devuelve el valor de esa función, sin embargo, no es válido durante el constructor. Por este motivo, se recomienda crear los agregados solo al reemplazar `CCmdTarget::OnCreateAggregates`, donde se puede confiar en el valor devuelto desde `GetControllingUnknown`, aunque se haya creado a partir de la implementación de `COleObjectFactory`.

También es importante que el objeto manipule el recuento de referencias correcto al agregar o liberar recuentos de referencias artificiales. Para asegurarse de que este sea el caso, llame siempre a `ExternalAddRef` y `ExternalRelease` en lugar de a `InternalRelease` y `InternalAddRef`. No es habitual llamar a `InternalRelease` o `InternalAddRef` en una clase compatible con la agregación.

## <a name="reference-material"></a>Material de referencia

El uso avanzado de OLE, que incluye definir sus propias interfaces o reemplazar la implementación del marco de trabajo de las interfaces de OLE, requiere el uso del mecanismo de mapa de interfaz subyacente.

En esta sección se describen las macros y las API que se usan para implementar estas características avanzadas.

### <a name="ccmdtargetenableaggregation--function-description"></a>CCmdTarget::EnableAggregation: descripción de la función

```cpp
void EnableAggregation();
```

#### <a name="remarks"></a>Notas

Llame a esta función en el constructor de la clase derivada si desea disponer de compatibilidad con la agregación OLE de objetos de este tipo. De este modo se prepara una implementación de IUnknown especial necesaria para objetos agregables.

### <a name="ccmdtargetexternalqueryinterface--function-description"></a>CCmdTarget::ExternalQueryInterface: descripción de la función

```cpp
DWORD ExternalQueryInterface(
    const void FAR* lpIID,
    LPVOIDFAR* ppvObj
);
```

#### <a name="parameters"></a>Parameters

*lpIID*<br/>
Un puntero lejano a un IID (el primer argumento para QueryInterface)

*ppvObj*<br/>
Un puntero a un IUnknown* (el segundo argumento para QueryInterface)

#### <a name="remarks"></a>Notas

Llame a esta función en la implementación de IUnknown para cada interfaz que implemente la clase. Esta función proporciona la implementación controlada por datos estándar de QueryInterface según el mapa de interfaz del objeto. Es necesario convertir el valor devuelto a un valor HRESULT. Si el objeto es agregado, esta función llamará al “IUnknown de control” en lugar de usar el mapa de interfaz local.

### <a name="ccmdtargetexternaladdref--function-description"></a>CCmdTarget::ExternalAddRef: descripción de la función

```cpp
DWORD ExternalAddRef();
```

#### <a name="remarks"></a>Notas

Llame a esta función en la implementación de IUnknown::AddRef para cada interfaz que implemente la clase. El valor devuelto es el nuevo recuento de referencias en el objeto CCmdTarget. Si el objeto es agregado, esta función llamará al “IUnknown de control” en lugar de manipular el recuento de referencias local.

### <a name="ccmdtargetexternalrelease--function-description"></a>CCmdTarget::ExternalRelease: descripción de la función

```cpp
DWORD ExternalRelease();
```

#### <a name="remarks"></a>Notas

Llame a esta función en la implementación de IUnknown::Release para cada interfaz que implemente la clase. El valor devuelto indica el nuevo recuento de referencias en el objeto. Si el objeto es agregado, esta función llamará al “IUnknown de control” en lugar de manipular el recuento de referencias local.

### <a name="declare_interface_map--macro-description"></a>DECLARE_INTERFACE_MAP: descripción de la macro

```cpp
DECLARE_INTERFACE_MAP
```

#### <a name="remarks"></a>Notas

Use esta macro en cualquier clase derivada de `CCmdTarget` que tendrá un mapa de interfaz. Se usa prácticamente de la misma manera que DECLARE_MESSAGE_MAP. Esta llamada de macro debe colocarse en la definición de clase, por lo general en un archivo de encabezado (.H). Una clase con DECLARE_INTERFACE_MAP debe definir el mapa de interfaz en el archivo de implementación (. CPP) con las macros BEGIN_INTERFACE_MAP y END_INTERFACE_MAP.

### <a name="begin_interface_part-and-end_interface_part--macro-descriptions"></a>BEGIN_INTERFACE_PART y END_INTERFACE_PART: descripciones de macros

```cpp
BEGIN_INTERFACE_PART(localClass, iface);
END_INTERFACE_PART(localClass)
```

#### <a name="parameters"></a>Parameters

*localClass*<br/>
El nombre de la clase que implementa la interfaz

*iface*<br/>
El nombre de la interfaz que implementa esta clase

#### <a name="remarks"></a>Notas

Para cada interfaz que va a implementar la clase, debe tener un par de BEGIN_INTERFACE_PART y END_INTERFACE_PART. Estas macros definen una clase local que se deriva de la interfaz OLE que defina, así como una variable miembro incrustada de esa clase. Los miembros [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref), [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)y [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) se declaran automáticamente. Debe incluir las declaraciones de las otras funciones miembro que forman parte de la interfaz que se está implementando (esas declaraciones se colocan entre las macros BEGIN_INTERFACE_PART y END_INTERFACE_PART).

El argumento *iFace* es la interfaz OLE que desea implementar, como `IAdviseSink`o `IPersistStorage` (o su propia interfaz personalizada).

El argumento *localClass* es el nombre de la clase local que se definirá. Una “X” se antepone al nombre automáticamente. Esta convención de nomenclatura se usa para evitar colisiones con clases globales del mismo nombre. Además, el nombre del miembro incrustado, el mismo que el nombre *localClass* , excepto que tiene el prefijo ' m_x '.

Por ejemplo:

```cpp
BEGIN_INTERFACE_PART(MyAdviseSink, IAdviseSink)
    STDMETHOD_(void, OnDataChange)(LPFORMATETC, LPSTGMEDIUM);
    STDMETHOD_(void, OnViewChange)(DWORD, LONG);
    STDMETHOD_(void, OnRename)(LPMONIKER);
    STDMETHOD_(void, OnSave)();
    STDMETHOD_(void, OnClose)();
END_INTERFACE_PART(MyAdviseSink)
```

El código anterior definiría una clase local llamada XMyAdviseSink derivada de IAdviseSink y un miembro de la clase en la que se declara llamado m_xMyAdviseSink. Nota:

> [!NOTE]
> Las líneas que comienzan por `STDMETHOD`_ se copian esencialmente desde OLE2. H y se modifican ligeramente. Copiarlas desde OLE2.H puede reducir los errores difíciles de resolver.

### <a name="begin_interface_map-and-end_interface_map--macro-descriptions"></a>BEGIN_INTERFACE_PART y END_INTERFACE_PART: descripciones de macros

```cpp
BEGIN_INTERFACE_MAP(theClass, baseClass)
END_INTERFACE_MAP
```

#### <a name="parameters"></a>Parameters

*Clase*<br/>
La clase en la que se debe definir el mapa de interfaz.

*baseClass*<br/>
La clase de la que se deriva la *clase* .

#### <a name="remarks"></a>Notas

Las macros BEGIN_INTERFACE_MAP y END_INTERFACE_MAP se usan en el archivo de implementación para definir realmente el mapa de interfaz. Para cada interfaz que se implementa, hay una o varias llamadas a macros INTERFACE_PART. Para cada agregado que utiliza la clase, hay una INTERFACE_AGGREGATE la invocación de macro.

### <a name="interface_part--macro-description"></a>INTERFACE_PART: descripción de la macro

```cpp
INTERFACE_PART(theClass, iid, localClass)
```

#### <a name="parameters"></a>Parameters

*Clase*<br/>
El nombre de la clase que contiene el mapa de interfaz.

*iid*<br/>
El `IID` que se debe asignar a la clase incrustada.

*localClass*<br/>
El nombre de la clase local (menos la “X”).

#### <a name="remarks"></a>Notas

Esta macro se utiliza entre la macro BEGIN_INTERFACE_MAP y la macro END_INTERFACE_MAP para cada interfaz que el objeto va a admitir. Permite asignar un IID a un miembro de la clase indicada por la *clase* y *localClass*. El ' m_x ' se agregará automáticamente a *localClass* . Tenga en cuenta que puede que haya más de un `IID` asociado a un único miembro. Esto es muy útil cuando se implementa únicamente una interfaz “más derivada” y se desea proporcionar todas las interfaces intermedias. Un buen ejemplo de esto es la interfaz `IOleInPlaceFrameWindow`. Su jerarquía tiene este aspecto:

```Hierarchy
IUnknown
    IOleWindow
        IOleUIWindow
            IOleInPlaceFrameWindow
```

Si un objeto implementa `IOleInPlaceFrameWindow`, un cliente puede `QueryInterface` en cualquiera de estas interfaces: `IOleUIWindow`, `IOleWindow`o [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown), además de la interfaz "más derivada" `IOleInPlaceFrameWindow` (la que realmente está implementando). Para controlar esto, puede usar más de una macro INTERFACE_PART para asignar cada una de las interfaces base a la interfaz `IOleInPlaceFrameWindow`:

en el archivo de definición de clase:

```cpp
BEGIN_INTERFACE_PART(CMyFrameWindow, IOleInPlaceFrameWindow)
```

en el archivo de implementación de clase:

```cpp
BEGIN_INTERFACE_MAP(CMyWnd, CFrameWnd)
    INTERFACE_PART(CMyWnd, IID_IOleWindow, MyFrameWindow)
    INTERFACE_PART(CMyWnd, IID_IOleUIWindow, MyFrameWindow)
    INTERFACE_PART(CMyWnd, IID_IOleInPlaceFrameWindow, MyFrameWindow)
END_INTERFACE_MAP
```

El marco de trabajo se encarga de IUnknown porque siempre se requiere.

### <a name="interface_part--macro-description"></a>INTERFACE_PART: descripción de la macro

```cpp
INTERFACE_AGGREGATE(theClass, theAggr)
```

#### <a name="parameters"></a>Parameters

*Clase*<br/>
El nombre de la clase que contiene el mapa de interfaz.

*theAggr*<br/>
El nombre de la variable miembro que se debe agregar.

#### <a name="remarks"></a>Notas

Esta macro se usa para indicar al marco de trabajo que la clase está usando un objeto agregado. Debe aparecer entre las macros BEGIN_INTERFACE_PART y END_INTERFACE_PART. Un objeto agregado es un objeto independiente, derivado de [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown). Mediante el uso de un agregado y la macro INTERFACE_AGGREGATE, puede hacer que el objeto admita directamente todas las interfaces que admite el agregado. El argumento *theAggr* es simplemente el nombre de una variable miembro de la clase que se deriva de [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) (directa o indirectamente). Todas las macros de INTERFACE_AGGREGATE deben seguir a las macros de INTERFACE_PART cuando se colocan en un mapa de interfaz.

## <a name="see-also"></a>Vea también

[Notas técnicas por número](../mfc/technical-notes-by-number.md)<br/>
[Notas técnicas por categoría](../mfc/technical-notes-by-category.md)
