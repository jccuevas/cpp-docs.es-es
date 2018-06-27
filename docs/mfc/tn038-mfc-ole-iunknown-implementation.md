---
title: 'TN038: Implementación de IUnknown en MFC OLE | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.mfc.ole
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f6a52846754bdf1293e03a47127ae8886e0f1cd2
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/26/2018
ms.locfileid: "36952435"
---
# <a name="tn038-mfcole-iunknown-implementation"></a>TN038: Implementación de IUnknown en MFC/OLE
> [!NOTE]
>  La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea. Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos. Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.  
  
 En el corazón de OLE 2 se encuentra el “Modelo de objetos componentes de OLE”, también conocido como COM. COM define un estándar sobre cómo se comunican entre sí los objetos al cooperar. Esto incluye los detalles relativos al aspecto que tiene un “objeto”, incluido el modo en que se envían los métodos en un objeto. COM también define una clase base de la que se derivan todas las clases compatibles con COM. Esta clase base es [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509). Aunque la [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) interfaz se conoce como una clase de C++, COM no es específico para ningún lenguaje, se puede implementar en C, PASCAL o cualquier otro lenguaje compatible con el diseño binario de un objeto COM.  
  
 OLE hace referencia a todas las clases derivadas de [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) como "interfaces". Se trata de una distinción importante, desde una "interfaz" como [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) no conlleva ninguna implementación. Simplemente define el protocolo por el que se comunican los objetos, no lo que hacen específicamente esas implementaciones. Esto es razonable para un sistema que permite la máxima flexibilidad. Es responsabilidad de MFC implementar un comportamiento predeterminado para programas escritos en MFC o C++.  
  
 Para entender la implementación de MFC de [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) primero debe entender qué es esta interfaz. Una versión simplificada de [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) se definen a continuación:  
  
```  
class IUnknown  
{  
public:  
    virtual HRESULT QueryInterface(REFIID iid, void** ppvObj) = 0;  
    virtual ULONG AddRef() = 0;  
    virtual ULONG Release() = 0;  
};  
```  
  
> [!NOTE]
>  Ciertos detalles necesarios de convención de llamada, como `__stdcall`, se dejan fuera de esta ilustración.  
  
 El [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379) y [versión](http://msdn.microsoft.com/library/windows/desktop/ms682317) funciones miembro controlan la administración de memoria del objeto. COM usa un esquema de recuento de referencias para realizar un seguimiento de los objetos. Nunca se hace referencia a un objeto directamente, como se hace en C++. En su lugar, siempre se hace referencia a los objetos COM a través de un puntero. Para liberar el objeto cuando el propietario haya terminado con él, el objeto [versión](http://msdn.microsoft.com/library/windows/desktop/ms682317) miembro se llama (en lugar de usar el operador delete, tal como se haría con un objeto de C++ convencional). El mecanismo de recuento de referencias permite administrar varias referencias a un único objeto. Una implementación de [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379) y [versión](http://msdn.microsoft.com/library/windows/desktop/ms682317) mantiene un recuento de referencias en el objeto, el objeto no se elimina hasta que su recuento de referencias llega a cero.  
  
 [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379) y [versión](http://msdn.microsoft.com/library/windows/desktop/ms682317) son bastante sencilla desde una perspectiva de implementación. A continuación se muestra una implementación trivial:  
  
```  
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
  
 El [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) función miembro es un poco más interesante. No resulta muy interesante tener un objeto cuyas únicas funciones miembro son [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379) y [versión](http://msdn.microsoft.com/library/windows/desktop/ms682317) , sería bueno indicarle al objeto que hiciese más cosas que [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) proporciona. Aquí es donde [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) es útil. Permite obtener una “interfaz” diferente en el mismo objeto. Estas interfaces se derivan normalmente de [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) y agregar funcionalidad adicional mediante la adición de nuevas funciones de miembro. Las interfaces COM nunca tienen variables miembro declaradas en la interfaz y todas las funciones miembro se declaran como virtuales puras. Por ejemplo,  
  
```  
class IPrintInterface : public IUnknown  
{  
public:  
    virtual void PrintObject() = 0;  
};  
```  
  
 Para obtener una IPrintInterface si solo tiene un [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509), llame a [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) mediante la `IID` de la `IPrintInterface`. Un `IID` es un número de 128 bits que identifica la interfaz de forma única. Hay un `IID` para cada interfaz que defina usted u OLE. Si *pUnk* es un puntero a un [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) de objeto, el código para recuperar una IPrintInterface podría ser:  
  
```  
IPrintInterface* pPrint = NULL;  
if (pUnk->QueryInterface(IID_IPrintInterface,   
 (void**)&pPrint) == NOERROR)  
{  
    pPrint->PrintObject();
pPrint->Release();
*// release pointer obtained via QueryInterface  
}  
```  
  
 Parece bastante sencillo, pero ¿cómo implementaría un objeto que admite tanto la IPrintInterface y [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) interfaz en este caso es simple ya que la IPrintInterface se deriva directamente de [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) : al implementar IPrintInterface, [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) se admite automáticamente. Por ejemplo:  
  
```  
class CPrintObj : public CPrintInterface  
{  
    virtual HRESULT QueryInterface(REFIID iid, void** ppvObj);

    virtual ULONG AddRef();
virtual ULONG Release();
virtual void PrintObject();

};  
```  
  
 Las implementaciones de [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379) y [versión](http://msdn.microsoft.com/library/windows/desktop/ms682317) podría ser exactamente el mismo que las implementadas anterior. `CPrintObj::QueryInterface` sería algo parecido a esto:  
  
```  
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
  
 Como puede ver, si se reconoce el identificador de interfaz (IID), se devuelve un puntero al objeto; de lo contrario, se produce un error. Tenga en cuenta también que una correcta [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) da como resultado un implícita [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379). Por supuesto, también debe implementar CEditObj::Print. Eso es sencillo porque la IPrintInterface se deriva directamente de la [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) interfaz. Sin embargo, si desea admitir dos interfaces diferentes, ambas derivadas de [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509), considere lo siguiente:  
  
```  
class IEditInterface : public IUnkown  
{  
public:  
    virtual void EditObject() = 0;  
};  
```  
  
 Aunque hay diferentes maneras de implementar una clase compatible con IEditInterface e IPrintInterface —por ejemplo, usar la herencia múltiple de C++—, aquí nos centraremos en el uso de las clases anidadas para implementar esta funcionalidad.  
  
```  
class CEditPrintObj  
{  
public:  
    CEditPrintObj();

 
    HRESULT QueryInterface(REFIID iid,
    void**);

    ULONG AddRef();
ULONG Release();
DWORD m_dwRef;  
 
    class CPrintObj : public IPrintInterface  
 {  
    public: 
    CEditPrintObj* m_pParent;  
    virtual HRESULT QueryInterface(REFIID iid,
    void** ppvObj);

    virtual ULONG AddRef();
virtual ULONG Release();

 } m_printObj;  
 
    class CEditObj : public IEditInterface  
 {  
    public: 
    CEditPrintObj* m_pParent;  
    virtual ULONG QueryInterface(REFIID iid,
    void** ppvObj);

    virtual ULONG AddRef();
virtual ULONG Release();

 } m_editObj;  
};  
```  
  
 A continuación se incluye la implementación al completo:  
  
```  
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
 
HRESULT CEditPrintObj::QueryInterface(REFIID iid,
    void** ppvObj)  
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
 
HRESULT CEditPrintObj::CEditObj::QueryInterface(
    REFIID iid,
    void** ppvObj)   
{   
    return m_pParent->QueryInterface(iid,
    ppvObj);

}  
 
ULONG CEditPrintObj::CPrintObj::AddRef()   
{   
    return m_pParent->AddRef();

}  
 
ULONG CEditPrintObj::CPrintObj::Release()   
{   
    return m_pParent->Release();

}  
 
HRESULT CEditPrintObj::CPrintObj::QueryInterface(
    REFIID iid,
    void** ppvObj)   
{   
    return m_pParent->QueryInterface(iid,
    ppvObj);

}  
```  
  
 Tenga en cuenta que la mayor parte de la [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) implementación se coloca en la clase CEditPrintObj en lugar de duplicar el código en ceditprintobj:: Ceditobj y ceditprintobj:: Cprintobj. Esto reduce la cantidad de código y evita errores. El punto clave aquí es que, de la interfaz IUnknown es posible llamar a [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) para recuperar cualquier interfaz podría admitir el objeto y de cada una de esas interfaces es posible hacer lo mismo. Esto significa que todos los [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) funciones disponibles desde cada interfaz deben se comportan exactamente igual. Para que estos objetos incrustados llamen a la implementación en el “objeto externo”, se usa un puntero (m_pParent). Se inicializa el puntero m_pParent durante el constructor CEditPrintObj. A continuación, debería implementar también CEditPrintObj::CPrintObj::PrintObject y CEditPrintObj::CEditObj::EditObject. Se agregó un poco de código para agregar una característica: la capacidad de editar el objeto. Afortunadamente, es bastante raro que las interfaces tengan solo una función miembro (aunque puede pasar) y, en este caso, lo normal sería que EditObject y PrintObject se combinasen en una única interfaz.  
  
 Esto requeriría una explicación muy larga y una gran cantidad de código para un escenario tan simple. Las clases de MFC/OLE proporcionan una alternativa más sencilla. La implementación de MFC usa una técnica similar a la forma en que los mensajes de Windows se ajustan con Mapas de mensajes. Esta función se denomina *mapas de interfaz* y se describe en la sección siguiente.  
  
## <a name="mfc-interface-maps"></a>Mapas de interfaz de MFC  
 MFC/OLE incluye una implementación de “Mapas de interfaz” similar a los “Mapas de mensajes” y “Mapas de envío” de MFC en cuanto a su concepto y ejecución. Las características principales de Mapas de interfaz de MFC son las siguientes:  
  
-   Una implementación estándar de [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509), integrada en el `CCmdTarget` clase.  
  
-   Mantenimiento del recuento de referencias, modificado por [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379) y [versión](http://msdn.microsoft.com/library/windows/desktop/ms682317)  
  
-   Implementación de controlada por datos [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521)  
  
 Además, los mapas de interfaz son compatibles con las siguientes características avanzadas:  
  
-   Compatibilidad con la creación de objetos COM agregables  
  
-   Compatibilidad con el uso de objetos agregados en la implementación de un objeto COM  
  
-   La implementación se puede enlazar y extender  
  
 Para obtener más información sobre la agregación, vea el [agregación](http://msdn.microsoft.com/library/windows/desktop/ms686558\(v=vs.85\).aspx) tema.  
  
 La compatibilidad con el mapa de interfaz de MFC se basa en la clase `CCmdTarget`. `CCmdTarget` "*tiene un*" hacen referencia a recuento, así como todas las funciones miembro asociadas con la [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) implementación (por ejemplo, el recuento de referencias es en `CCmdTarget`). Para crear una clase compatible con OLE y COM, derive una clase de `CCmdTarget` y use varias macros, así como funciones miembro de `CCmdTarget` para implementar las interfaces deseadas. La implementación de MFC usa clases anidadas para definir cada implementación de interfaz de manera muy similar al ejemplo anterior. Esto se facilita mediante una implementación estándar de IUnknown y mediante varias macros que eliminan parte del código repetitivo.  
  
## <a name="interface-map-basics"></a>Conceptos básicos de mapa de interfaz  
  
#### <a name="to-implement-a-class-using-mfcs-interface-maps"></a>Para implementar una clase mediante los mapas de interfaz de MFC  
  
1.  Derive una clase directa o indirectamente de `CCmdTarget`.  
  
2.  Use la función `DECLARE_INTERFACE_MAP` en la definición de la clase derivada.  
  
3.  Para cada interfaz que se va a admitir, use las macros BEGIN_INTERFACE_PART y END_INTERFACE_PART en la definición de clase.  
  
4.  En el archivo de implementación, use las macros begin_interface_part y end_interface_part para definir el mapa de interfaz de la clase.  
  
5.  Para cada IID compatible, use la macro INTERFACE_PART entre las macros begin_interface_part y end_interface_part para asignar ese IID a una "parte" de la clase específica.  
  
6.  Implemente cada una de las clases anidadas que representan las interfaces con las que se ofrece compatibilidad.  
  
7.  Utilice la macro METHOD_PROLOGUE para tener acceso a la principal, `CCmdTarget`-objeto derivado.  
  
8. [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379), [versión](http://msdn.microsoft.com/library/windows/desktop/ms682317), y [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) puede delegar en el `CCmdTarget` implementación de estas funciones (`ExternalAddRef`, `ExternalRelease`, y `ExternalQueryInterface`).  
  
 El ejemplo CPrintEditObj expuesto anteriormente podría implementarse de la siguiente manera:  
  
```  
class CPrintEditObj : public CCmdTarget  
{  
public: *// member data and member functions for CPrintEditObj go here  
 
// Interface Maps  
protected:  
    DECLARE_INTERFACE_MAP() 
 
    BEGIN_INTERFACE_PART(EditObj,
    IEditInterface)  
    STDMETHOD_(void,
    EditObject)();
END_INTERFACE_PART(EditObj) 
 
    BEGIN_INTERFACE_PART(PrintObj,
    IPrintInterface)  
    STDMETHOD_(void,
    PrintObject)();
END_INTERFACE_PART(PrintObj) 
};  
```  
  
 La declaración anterior crea una clase derivada de `CCmdTarget`. La macro DECLARE_INTERFACE_MAP indica al marco que esta clase tendrá un mapa de interfaz personalizada. Además, las macros BEGIN_INTERFACE_PART y END_INTERFACE_PART definen clases anidadas, en este caso con nombres CEditObj y CPrintObj (la X se usa solo para diferenciar las clases anidadas de clases globales que comiencen con "C" y la interfaz de clases que empiecen por "I"). Se crean dos miembros anidados de estas clases: m_CEditObj y m_CPrintObj, respectivamente. Las macros declaran automáticamente el [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379), [versión](http://msdn.microsoft.com/library/windows/desktop/ms682317), y [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) funciones; por lo tanto, solo declara las funciones específicas de esta interfaz: EditObject y PrintObject (la macro OLE STDMETHOD sirve para que **_stdcall** y las palabras clave virtuales se proporcionan como adecuado para la plataforma de destino).  
  
 Para implementar el mapa de interfaz para esta clase:  
  
```  
BEGIN_INTERFACE_MAP(CPrintEditObj,
    CCmdTarget)  
    INTERFACE_PART(CPrintEditObj,
    IID_IPrintInterface,
    PrintObj)  
    INTERFACE_PART(CPrintEditObj,
    IID_IEditInterface,
    EditObj)  
END_INTERFACE_MAP()  
```  
  
 Esto conectará el IID IID_IPrintInterface con m_CPrintObj e IID_IEditInterface con m_CEditObj respectivamente. El `CCmdTarget` implementación de [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) (`CCmdTarget::ExternalQueryInterface`) esta asignación se utiliza para devolver punteros a m_CPrintObj y a m_CEditObj cuando se solicite. No es necesario incluir una entrada para `IID_IUnknown`; el marco de trabajo usará la primera interfaz del mapa (en este caso, m_CPrintObj) cuando `IID_IUnknown` se solicita.  
  
 Aunque la macro BEGIN_INTERFACE_PART se declara automáticamente el [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379), [versión](http://msdn.microsoft.com/library/windows/desktop/ms682317) y [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) funciones para usted, deberá implementarlos:  
  
```  
ULONG FAR EXPORT CEditPrintObj::XEditObj::AddRef()  
{  
    METHOD_PROLOGUE(CEditPrintObj,
    EditObj)  
    return pThis->ExternalAddRef();

}  
 
ULONG FAR EXPORT CEditPrintObj::XEditObj::Release()  
{  
    METHOD_PROLOGUE(CEditPrintObj,
    EditObj)  
    return pThis->ExternalRelease();

}  
 
HRESULT FAR EXPORT CEditPrintObj::XEditObj::QueryInterface(
    REFIID iid,
    void FAR* FAR* ppvObj)  
{  
    METHOD_PROLOGUE(CEditPrintObj,
    EditObj)  
    return (HRESULT)pThis->ExternalQueryInterface(&iid,
    ppvObj);

}  
 
void FAR EXPORT CEditPrintObj::XEditObj::EditObject()  
{  
    METHOD_PROLOGUE(CEditPrintObj,
    EditObj) *// code to "Edit" the object,
    whatever that means...  
}  
```  
  
 La implementación de CEditPrintObj::CPrintObj sería similar a las definiciones anteriores de CEditPrintObj::CEditObj. Aunque sería posible crear una macro que pudiese generar automáticamente estas funciones (este era el caso en etapas anteriores del desarrollo de MFC/OLE), resulta difícil establecer puntos de interrupción cuando una macro genera más de una línea de código. Por este motivo, este código se expande manualmente.  
  
 Mediante el uso de la implementación del marco de trabajo de mapas de mensajes, no se tuvieron que realizar varias cosas:  
  
-   Implementar QueryInterface  
  
-   Implementar AddRef y Release  
  
-   Declarar cualquiera de estos métodos integrados en ambas interfaces  
  
 Además el marco de trabajo usa mapas de mensajes internamente. Esto le permite derivar una clase de marco de trabajo, como, por ejemplo, `COleServerDoc`, que ya es compatible con determinadas interfaces y proporciona reemplazos o adiciones a las interfaces proporcionadas por el marco de trabajo. Puede hacerlo porque el marco de trabajo es totalmente compatible con la herencia de un mapa de interfaz a partir de una clase base. Este es el motivo por qué BEGIN_INTERFACE_MAP toma como su segundo parámetro el nombre de la clase base.  
  
> [!NOTE]
>  Por lo general, no es posible reutilizar las implementaciones integradas de las interfaces OLE simplemente heredando la especialización incrustada de esa interfaz a partir de la versión MFC. Esto no es posible porque el uso de la macro METHOD_PROLOGUE para obtener acceso a la que contiene `CCmdTarget`-objeto derivado implica un *desplazamiento fijo* del objeto incrustado desde el `CCmdTarget`-objeto derivado. Esto significa, por ejemplo, que no puede derivar un XMyAdviseSink incrustado de la implementación de MFC en `COleClientItem::XAdviseSink`, porque XAdviseSink se basa en estar a un desplazamiento específico de la parte superior del objeto `COleClientItem`.  
  
> [!NOTE]
>  Sin embargo, puede delegar en la implementación de MFC para todas las funciones que desee que tengan el comportamiento predeterminado de MFC. Esto se hace en la implementación de MFC de `IOleInPlaceFrame` (XOleInPlaceFrame) en la clase `COleFrameHook` (delega en m_xOleInPlaceUIWindow para muchas funciones). Este diseño se ha elegido para reducir el tamaño en tiempo de ejecución de objetos que implementan muchas interfaces; elimina la necesidad de un puntero (tal como se usaba m_pParent en la sección anterior).  
  
### <a name="aggregation-and-interface-maps"></a>Agregación y mapas de interfaz  
 Además de ser compatible con objetos COM independientes, MFC también es compatible con la agregación. Agregación es un tema demasiado complejo para discutirlo aquí; hacer referencia a la [agregación](http://msdn.microsoft.com/library/windows/desktop/ms686558\(v=vs.85\).aspx) tema para obtener más información sobre la agregación. Esta nota solo describe la compatibilidad con la agregación que se encuentra integrada en el marco de trabajo y los mapas de interfaz.  
  
 Hay dos maneras de utilizar la agregación: (1) usando un objeto COM compatible con la agregación e (2) implementando un objeto que pueda ser agregado por otro objeto. Estas capacidades se pueden denominar como “usar un objeto agregado” y “hacer que un objeto sea agregable”. MFC es compatible con ambas capacidades.  
  
### <a name="using-an-aggregate-object"></a>Usar un objeto agregado  
 Para usar un objeto agregado, debe haber alguna manera de asociar el agregado en el mecanismo de QueryInterface. En otras palabras, el objeto agregado debe comportarse como si fuera una parte nativa del objeto. Entonces, ¿cómo este valor equivalente en el mecanismo de mapa de interfaz de MFC además INTERFACE_PART (macro), donde un objeto anidado se asigna a un IID, también puede declarar un objeto agregado como parte de su `CCmdTarget` clase derivada. Para ello, se utiliza la macro INTERFACE_AGGREGATE. Esto le permite especificar una variable de miembro (que debe ser un puntero a un [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) o clase derivada), que consiste en que se integrarán en el mecanismo de mapa de interfaz. Si el puntero no es nulo cuando `CCmdTarget::ExternalQueryInterface` es llama, el marco de trabajo llamará automáticamente el objeto agregado [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) función miembro, si la `IID` solicitado no es uno de nativo `IID`s compatible con la `CCmdTarget` propio objeto.  
  
##### <a name="to-use-the-interfaceaggregate-macro"></a>Para usar la macro INTERFACE_AGGREGATE  
  
1.  Declare una variable miembro (una `IUnknown*`) que contenga un puntero al objeto agregado.  
  
2.  Incluya una macro INTERFACE_AGGREGATE en el mapa de interfaz, que hace referencia a la variable miembro por su nombre.  
  
3.  En algún momento (normalmente durante `CCmdTarget::OnCreateAggregates`), inicialice la variable miembro en un valor que no sea NULL.  
  
 Por ejemplo:  
  
```  
class CAggrExample : public CCmdTarget  
{  
public:  
    CAggrExample();

 
protected:  
    LPUNKNOWN m_lpAggrInner;  
    virtual BOOL OnCreateAggregates();

 
    DECLARE_INTERFACE_MAP() *// "native" interface part macros may be used here  
};  
 
CAggrExample::CAggrExample()  
{  
    m_lpAggrInner = NULL;  
}  
 
BOOL CAggrExample::OnCreateAggregates()  
{ *// wire up aggregate with correct controlling unknown  
    m_lpAggrInner = CoCreateInstance(CLSID_Example,  
    GetControllingUnknown(),
    CLSCTX_INPROC_SERVER,  
    IID_IUnknown, (LPVOID*)&m_lpAggrInner);

    if (m_lpAggrInner == NULL)  
    return FALSE; *// optionally,
    create other aggregate objects here  
    return TRUE;  
}  
 
BEGIN_INTERFACE_MAP(CAggrExample,
    CCmdTarget) *// native "INTERFACE_PART" entries go here  
    INTERFACE_AGGREGATE(CAggrExample,
    m_lpAggrInner)  
END_INTERFACE_MAP()  
```  
  
 La variable m_lpAggrInner se inicializa en el constructor con un valor NULL. El marco de trabajo pasa por alto una variable de miembro NULL en la implementación predeterminada de [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521). `OnCreateAggregates` es un buen lugar para crear realmente los objetos agregados. Tendrá que llamarlo explícitamente si va a crear el objeto fuera de la implementación de MFC de `COleObjectFactory`. La razón para crear agregados en `CCmdTarget::OnCreateAggregates`, así como el uso de `CCmdTarget::GetControllingUnknown`, serán evidentes al crear objetos agregables.  
  
 Esta técnica le dará su objeto de todas las interfaces compatibles con el objeto agregado además de sus interfaces nativas. Si solo quiere un subconjunto de las interfaces compatibles con el agregado, puede invalidar `CCmdTarget::GetInterfaceHook`. Esto le permite hookability muy bajo nivel, similar a [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521). Lo normal es querer todas las interfaces que sean compatibles con el agregado.  
  
### <a name="making-an-object-implementation-aggregatable"></a>Convertir en agregable una implementación de objeto  
 Para un objeto sea agregable, la implementación de [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379), [versión](http://msdn.microsoft.com/library/windows/desktop/ms682317), y [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) deben delegar en "desconocido de control". En otras palabras, para que forme parte del objeto, debe delegar [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379), [versión](http://msdn.microsoft.com/library/windows/desktop/ms682317), y [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) en un objeto diferente, también derivado de [ IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509). Este “desconocido de control” se proporciona al objeto cuando se crea, es decir, se proporciona a la implementación de `COleObjectFactory`. Esta implementación implica una pequeña cantidad de sobrecarga y en algunos casos no es deseable, por lo que MFC hace que sea opcional. Para hacer que un objeto sea agregable, se debe llamar a `CCmdTarget::EnableAggregation` desde el constructor del objeto.  
  
 Si el objeto también utiliza agregados, asegúrese de pasar el “desconocido de control” correcto a los objetos agregados. Normalmente esto [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) puntero se pasa al objeto cuando se crea el agregado. Por ejemplo, el parámetro pUnkOuter es el “desconocido de control” para los objetos creados con `CoCreateInstance`. El puntero correcto “desconocido de control” se puede recuperar llamando a `CCmdTarget::GetControllingUnknown`. Devuelve el valor de esa función, sin embargo, no es válido durante el constructor. Por este motivo, se recomienda crear los agregados solo al reemplazar `CCmdTarget::OnCreateAggregates`, donde se puede confiar en el valor devuelto desde `GetControllingUnknown`, aunque se haya creado a partir de la implementación de `COleObjectFactory`.  
  
 También es importante que el objeto manipule el recuento de referencias correcto al agregar o liberar recuentos de referencias artificiales. Para asegurarse de que este sea el caso, llame siempre a `ExternalAddRef` y `ExternalRelease` en lugar de a `InternalRelease` y `InternalAddRef`. No es habitual llamar a `InternalRelease` o `InternalAddRef` en una clase compatible con la agregación.  
  
### <a name="reference-material"></a>Material de referencia  
 El uso avanzado de OLE, que incluye definir sus propias interfaces o reemplazar la implementación del marco de trabajo de las interfaces de OLE, requiere el uso del mecanismo de mapa de interfaz subyacente.  
  
 En esta sección se describen las macros y las API que se usan para implementar estas características avanzadas.  
  
### <a name="ccmdtargetenableaggregation--function-description"></a>CCmdTarget::EnableAggregation: descripción de la función  
  
```  
 
void EnableAggregation();

 
```  
  
## <a name="remarks"></a>Comentarios  
 Llame a esta función en el constructor de la clase derivada si desea disponer de compatibilidad con la agregación OLE de objetos de este tipo. De este modo se prepara una implementación de IUnknown especial necesaria para objetos agregables.  
  
### <a name="ccmdtargetexternalqueryinterface--function-description"></a>CCmdTarget::ExternalQueryInterface: descripción de la función  
  
```  
 
    DWORD ExternalQueryInterface(constvoidFAR* lpIID, LPVOIDFAR* ppvObj);
```  
  
## <a name="remarks"></a>Comentarios  
  
#### <a name="parameters"></a>Parámetros  
 *lpIID*  
 Un puntero lejano a un IID (el primer argumento para QueryInterface)  
  
 *ppvObj*  
 Un puntero a un IUnknown* (el segundo argumento para QueryInterface)  
  
## <a name="remarks"></a>Comentarios  
 Llame a esta función en la implementación de IUnknown para cada interfaz que implemente la clase. Esta función proporciona la implementación controlada por datos estándar de QueryInterface según el mapa de interfaz del objeto. Es necesario convertir el valor devuelto a un valor HRESULT. Si el objeto es agregado, esta función llamará al “IUnknown de control” en lugar de usar el mapa de interfaz local.  
  
### <a name="ccmdtargetexternaladdref--function-description"></a>CCmdTarget::ExternalAddRef: descripción de la función  
  
```  
 
DWORD ExternalAddRef();

 
```  
  
## <a name="remarks"></a>Comentarios  
 Llame a esta función en la implementación de IUnknown::AddRef para cada interfaz que implemente la clase. El valor devuelto es el nuevo recuento de referencias en el objeto CCmdTarget. Si el objeto es agregado, esta función llamará al “IUnknown de control” en lugar de manipular el recuento de referencias local.  
  
### <a name="ccmdtargetexternalrelease--function-description"></a>CCmdTarget::ExternalRelease: descripción de la función  
  
```  
 
DWORD ExternalRelease();

 
```  
  
## <a name="remarks"></a>Comentarios  
 Llame a esta función en la implementación de IUnknown::Release para cada interfaz que implemente la clase. El valor devuelto indica el nuevo recuento de referencias en el objeto. Si el objeto es agregado, esta función llamará al “IUnknown de control” en lugar de manipular el recuento de referencias local.  
  
### <a name="declareinterfacemap--macro-description"></a>DECLARE_INTERFACE_MAP: descripción de la macro  
  
```  
 
DECLARE_INTERFACE_MAP  
 
```  
  
## <a name="remarks"></a>Comentarios  
 Use esta macro en cualquier clase derivada de `CCmdTarget` que tendrá un mapa de interfaz. Usar prácticamente la misma manera que DECLARE_MESSAGE_MAP. Esta llamada de macro debe colocarse en la definición de clase, por lo general en un archivo de encabezado (.H). Una clase con DECLARE_INTERFACE_MAP debe definir el mapa de interfaz en el archivo de implementación (. CPP) con las macros begin_interface_part y end_interface_part.  
  
### <a name="begininterfacepart-and-endinterfacepart--macro-descriptions"></a>BEGIN_INTERFACE_PART y END_INTERFACE_PART: descripciones de macros  
  
```  
 
    BEGIN_INTERFACE_PART(
 localClass,   
    iface);

END_INTERFACE_PART(
 localClass)  
```  
  
## <a name="remarks"></a>Comentarios  
  
#### <a name="parameters"></a>Parámetros  
 *localClass*  
 El nombre de la clase que implementa la interfaz  
  
 *iface*  
 El nombre de la interfaz que implementa esta clase  
  
## <a name="remarks"></a>Comentarios  
 Para cada interfaz que implementará la clase, debe disponer de un par BEGIN_INTERFACE_PART y END_INTERFACE_PART. Estas macros definen una clase local que se deriva de la interfaz OLE que defina, así como una variable miembro incrustada de esa clase. El [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379), [versión](http://msdn.microsoft.com/library/windows/desktop/ms682317), y [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) miembros se declaran automáticamente. Debe incluir las declaraciones de las demás funciones miembro que forman parte de la interfaz que se va a implementar (estas declaraciones se colocan entre las macros BEGIN_INTERFACE_PART y END_INTERFACE_PART).  
  
 El *iface* argumento es la interfaz OLE que se va a implementar, como `IAdviseSink`, o `IPersistStorage` (o su propia interfaz personalizada).  
  
 El *localClass* argumento es el nombre de la clase local que se definirá. Una “X” se antepone al nombre automáticamente. Esta convención de nomenclatura se usa para evitar colisiones con clases globales del mismo nombre. Además, el nombre del miembro incrustado, es el mismo que el *localClass* nombre salvo que lleva el prefijo "m_x".  
  
 Por ejemplo:  
  
```  
BEGIN_INTERFACE_PART(MyAdviseSink,
    IAdviseSink)  
    STDMETHOD_(void,
    OnDataChange)(LPFORMATETC,
    LPSTGMEDIUM);

    STDMETHOD_(void,
    OnViewChange)(DWORD,
    LONG);

    STDMETHOD_(void,
    OnRename)(LPMONIKER);

 STDMETHOD_(void,
    OnSave)();
STDMETHOD_(void,
    OnClose)();

END_INTERFACE_PART(MyAdviseSink) 
```  
  
 El código anterior definiría una clase local llamada XMyAdviseSink derivada de IAdviseSink y un miembro de la clase en la que se declara llamado m_xMyAdviseSink. Nota:  
  
> [!NOTE]
>  Las líneas que comienzan con `STDMETHOD`_ básicamente se copian desde OLE2. H y se modifican ligeramente. Copiarlas desde OLE2.H puede reducir los errores difíciles de resolver.  
  
### <a name="begininterfacemap-and-endinterfacemap--macro-descriptions"></a>BEGIN_INTERFACE_PART y END_INTERFACE_PART: descripciones de macros  
  
```  
 
    BEGIN_INTERFACE_MAP(
 theClass,   
    baseClass)END_INTERFACE_MAP 
```  
  
## <a name="remarks"></a>Comentarios  
  
#### <a name="parameters"></a>Parámetros  
 *theClass*  
 La clase en la que se debe definir el mapa de interfaz.  
  
 *baseClass*  
 La clase de la cual *theClass* deriva.  
  
## <a name="remarks"></a>Comentarios  
 Las macros begin_interface_part y end_interface_part se utilizan en el archivo de implementación para definir realmente el mapa de interfaz. Para cada interfaz que se implementa hay una o varias llamadas de macro INTERFACE_PART. Para cada función de agregado que usa la clase, hay una llamada de macro INTERFACE_AGGREGATE.  
  
### <a name="interfacepart--macro-description"></a>INTERFACE_PART: descripción de la macro  
  
```  
 
    INTERFACE_PART(
 theClass,   
    iid, 
    localClass) 
```  
  
## <a name="remarks"></a>Comentarios  
  
#### <a name="parameters"></a>Parámetros  
 *theClass*  
 El nombre de la clase que contiene el mapa de interfaz.  
  
 *IID*  
 El `IID` que se debe asignar a la clase incrustada.  
  
 *localClass*  
 El nombre de la clase local (menos la “X”).  
  
## <a name="remarks"></a>Comentarios  
 Esta macro se usa entre el BEGIN_INTERFACE_MAP (macro) y la macro END_INTERFACE_MAP para cada interfaz será compatible con el objeto. Permite asignar un IID a un miembro de la clase indicada por *theClass* y *localClass*. El elemento 'm_x' se agregará a la *localClass* automáticamente. Tenga en cuenta que puede que haya más de un `IID` asociado a un único miembro. Esto es muy útil cuando se implementa únicamente una interfaz “más derivada” y se desea proporcionar todas las interfaces intermedias. Un buen ejemplo de esto es la interfaz `IOleInPlaceFrameWindow`. Su jerarquía tiene este aspecto:  
  
```  
IUnknown  
    IOleWindow 
    IOleUIWindow 
    IOleInPlaceFrameWindow 
```  
  
 Si un objeto implementa `IOleInPlaceFrameWindow`, un cliente puede `QueryInterface` en cualquiera de estas interfaces: `IOleUIWindow`, `IOleWindow`, o [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509), además de la interfaz "más derivada" `IOleInPlaceFrameWindow` (lo están realmente implementar). En estos casos se puede utilizar más de una macro INTERFACE_PART para asignar cada interfaz base para la `IOleInPlaceFrameWindow` interfaz:  
  
 en el archivo de definición de clase:  
  
```  
BEGIN_INTERFACE_PART(CMyFrameWindow, IOleInPlaceFrameWindow)  
```  
  
 en el archivo de implementación de clase:  
  
```  
BEGIN_INTERFACE_MAP(CMyWnd,
    CFrameWnd)  
    INTERFACE_PART(CMyWnd,
    IID_IOleWindow,
    MyFrameWindow)  
    INTERFACE_PART(CMyWnd,
    IID_IOleUIWindow,
    MyFrameWindow)  
    INTERFACE_PART(CMyWnd,
    IID_IOleInPlaceFrameWindow,
    MyFrameWindow)  
END_INTERFACE_MAP  
```  
  
 El marco de trabajo se encarga de IUnknown porque siempre se requiere.  
  
### <a name="interfacepart--macro-description"></a>INTERFACE_PART: descripción de la macro  
  
```  
 
    INTERFACE_AGGREGATE(
 theClass,   
    theAggr) 
```  
  
## <a name="remarks"></a>Comentarios  
  
#### <a name="parameters"></a>Parámetros  
 *theClass*  
 El nombre de la clase que contiene el mapa de interfaz.  
  
 *theAggr*  
 El nombre de la variable miembro que se debe agregar.  
  
## <a name="remarks"></a>Comentarios  
 Esta macro se usa para indicar al marco de trabajo que la clase está usando un objeto agregado. Debe aparecer entre las macros BEGIN_INTERFACE_PART y END_INTERFACE_PART. Un objeto agregado es un objeto independiente, que se deriva de [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509). Al usar un agregado y la macro INTERFACE_AGGREGATE, puede realizar todas las interfaces que admita el agregado parece ser directamente compatibles con el objeto. El *theAggr* argumento es simplemente el nombre de una variable de miembro de la clase que se deriva de [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) (directa o indirectamente). Todas las macros INTERFACE_AGGREGATE deben seguir las macros INTERFACE_PART cuando se coloca en un mapa de interfaz.  
  
## <a name="see-also"></a>Vea también  
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)

