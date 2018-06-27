---
title: 'TN039: Implementación de automatización OLE de MFC | Documentos de Microsoft'
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
- MFC, COM support
- IDispatch interface
- MFC, OLE DB and
- TN039
- Automation, MFC COM interface entry points
ms.assetid: 765fa3e9-dd54-4f08-9ad2-26e0546ff8b6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 97c42f59042490f6408fb457b12f4bdb1a2eeb88
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/26/2018
ms.locfileid: "36953365"
---
# <a name="tn039-mfcole-automation-implementation"></a>TN039: Implementación de Automation MFC/OLE
> [!NOTE]
>  La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea. Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos. Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.  
  
## <a name="overview-of-ole-idispatch-interface"></a>Información general de la interfaz de IDispatch OLE  
 La `IDispatch` interfaz es el medio por el que las aplicaciones exponen métodos y propiedades que otras aplicaciones, como Visual BASIC u otros lenguajes, pueden hacer uso de características de la aplicación. La parte más importante de esta interfaz es la `IDispatch::Invoke` (función). MFC utiliza "mapas de envío" para implementar `IDispatch::Invoke`. El mapa de envíos proporciona la información de implementación de MFC en el diseño o la "forma" de la `CCmdTarget`-las clases derivadas, por ejemplo, que puede manipular las propiedades del objeto directamente o llamar a funciones dentro de su objeto a satisfacer miembro `IDispatch::Invoke` solicitudes.  
  
 En su mayor parte, ClassWizard y MFC cooperan para ocultar la mayoría de los detalles de automatización OLE desde el programador de aplicaciones. El programador se concentra en la funcionalidad real para exponer en la aplicación y no tiene que preocuparse de la mecánica subyacente.  
  
 Hay casos, sin embargo, donde es necesaria para comprender lo que MFC está haciendo en segundo plano. Esta nota abordará cómo el marco de trabajo asigna **DISPID**s a funciones miembro y propiedades. Conocimiento del algoritmo de MFC utiliza para asignar **DISPID**s solo es necesario cuando necesita conocer los identificadores, como cuando se crea una biblioteca de tipos"" para los objetos de la aplicación.  
  
## <a name="mfc-dispid-assignment"></a>Asignación de MFC DISPID  
 Aunque el usuario final de la automatización (un usuario de Visual Basic, por ejemplo), verá los nombres reales de la automatización habilita propiedades y métodos en su código (por ejemplo, obj. ShowWindow), la implementación de `IDispatch::Invoke` no recibe los nombres reales. Por motivos de optimización, recibe un **DISPID**, que es de 32 bits "mágica cookie" que describe el método o propiedad que se tiene acceso. Estos **DISPID** valores se devuelven de la `IDispatch` implementación a través de otro método, denominado `IDispatch::GetIDsOfNames`. Llame una aplicación de cliente de automatización `GetIDsOfNames` una vez por cada miembro o propiedad intenta obtener acceso y almacenarlos en memoria caché para llamadas posteriores a `IDispatch::Invoke`. De esta manera, la búsqueda de cadena costoso es solo realiza una vez por cada uso de objetos, en lugar de una vez por `IDispatch::Invoke` llamar.  
  
 MFC determina la **DISPID**de cada método y propiedad basados en dos cosas:  
  
-   La distancia desde la parte superior del mapa de envíos (1 relativo)  
  
-   La distancia del mapa de envíos de la clase más derivada (0 relativa)  
  
 El **DISPID** se divide en dos partes. El **LOWORD** de la **DISPID** contiene el primer componente, la distancia desde la parte superior del mapa de envíos. El **HIWORD** contiene la distancia desde la clase más derivada. Por ejemplo:  
  
```  
class CDispPoint : public CCmdTarget  
{  
public:  
    short m_x,
    m_y;  
 ...  
    DECLARE_DISPATCH_MAP() 
 ...  
};  
 
class CDisp3DPoint : public CDispPoint  
{  
public:  
    short m_z;  
 ...  
    DECLARE_DISPATCH_MAP() 
 ...  
};  
 
BEGIN_DISPATCH_MAP(CDispPoint,
    CCmdTarget)  
    DISP_PROPERTY(CDispPoint, "x",
    m_x,
    VT_I2)  
    DISP_PROPERTY(CDispPoint, "y",
    m_y,
    VT_I2)  
END_DISPATCH_MAP()  
 
BEGIN_DISPATCH_MAP(CDisp3DPoint,
    CDispPoint)  
    DISP_PROPERTY(CDisp3DPoint, "z",
    m_z,
    VT_I2)  
END_DISPATCH_MAP()  
```  
  
 Como puede ver, hay dos clases, ambos de los cuales exponen interfaces de automatización OLE. Una de estas clases se deriva de la otra y así aprovecha la funcionalidad de la clase base, incluido el elemento de automatización OLE ("x" e "y" propiedades en este caso).  
  
 MFC generará **DISPID**s para la clase CDispPoint como se indica a continuación:  
  
```  
property X    (DISPID)0x00000001  
property Y    (DISPID)0x00000002  
```  
  
 Dado que las propiedades no están en una clase base, el **HIWORD** de la **DISPID** siempre es cero (la distancia desde la clase más derivada para CDispPoint es cero).  
  
 MFC generará **DISPID**s para la clase CDisp3DPoint como se indica a continuación:  
  
```  
property Z    (DISPID)0x00000001  
property X    (DISPID)0x00010001  
property Y    (DISPID)0x00010002  
```  
  
 La propiedad Z se proporciona un **DISPID** con un cero **HIWORD** desde que se define en la clase que expone las propiedades, CDisp3DPoint. Puesto que las propiedades X e Y se definen en una clase base, el **HIWORD** de la **DISPID** es 1, ya que es la clase en que se definen estas propiedades a una distancia de una derivación de la clase más derivada.  
  
> [!NOTE]
>  El **LOWORD** siempre viene determinado por la posición en la asignación, incluso si existen entradas en el mapa con explícita **DISPID** (vea la sección siguiente para obtener información sobre la **_ID** versiones de la `DISP_PROPERTY` y `DISP_FUNCTION` macros).  
  
## <a name="advanced-mfc-dispatch-map-features"></a>MFC envío mapa características avanzadas  
 Hay una serie de características adicionales que no es compatible con ClassWizard con esta versión de Visual C++. Admite ClassWizard `DISP_FUNCTION`, `DISP_PROPERTY`, y `DISP_PROPERTY_EX` que definen un método, la propiedad de variable de miembro y la propiedad de función de miembro get/set, respectivamente. Estas capacidades suelen ser todo lo que necesita para crear la mayoría de los servidores de automatización.  
  
 Se pueden usar las siguientes macros adicionales cuando las macros de ClassWizard compatibles no son adecuadas: `DISP_PROPERTY_NOTIFY`, y `DISP_PROPERTY_PARAM`.  
  
## <a name="disppropertynotify--macro-description"></a>DISP_PROPERTY_NOTIFY: Descripción de la Macro  
  
```  
 
    DISP_PROPERTY_NOTIFY(
 theClass,   
    pszName, 
    memberName, 
    pfnAfterSet, 
    vtPropType) 
```  
  
## <a name="remarks"></a>Comentarios  
  
### <a name="parameters"></a>Parámetros  
 *theClass*  
 Nombre de la clase.  
  
 *pszName*  
 Nombre externo de la propiedad.  
  
 *nombre de usuario registrado*  
 Nombre de la variable de miembro en el que se almacena la propiedad.  
  
 *pfnAfterSet*  
 Nombre de función de miembro que se llamará cuando se cambia la propiedad.  
  
 *vtPropType*  
 Valor que especifica el tipo de propiedad.  
  
## <a name="remarks"></a>Comentarios  
 Esta macro es muy similar DISP_PROPERTY, salvo que acepta un argumento adicional. El argumento adicional, *pfnAfterSet,* debe ser una función miembro que no devuelve nada y no toma ningún parámetro, 'void OnPropertyNotify()'. Se le llamará **después** se ha modificado la variable miembro.  
  
## <a name="disppropertyparam--macro-description"></a>DISP_PROPERTY_PARAM: Descripción de la Macro  
  
```  
 
    DISP_PROPERTY_PARAM(
 theClass,   
    pszName, 
    pfnGet, 
    pfnSet, 
    vtPropType, 
    vtsParams) 
```  
  
## <a name="remarks"></a>Comentarios  
  
### <a name="parameters"></a>Parámetros  
 *theClass*  
 Nombre de la clase.  
  
 *pszName*  
 Nombre externo de la propiedad.  
  
 *memberGet*  
 Nombre de la función de miembro que se utiliza para obtener la propiedad.  
  
 *conjunto de miembros*  
 Nombre de la función de miembro que se usa para establecer la propiedad.  
  
 *vtPropType*  
 Valor que especifica el tipo de propiedad.  
  
 *vtsParams*  
 Una cadena de espacio separados VTS_ para cada parámetro.  
  
## <a name="remarks"></a>Comentarios  
 Mucho al igual que la macro DISP_PROPERTY_EX, esta macro define una propiedad que se obtiene acceso con funciones de miembro Get y Set independientes. Esta macro, sin embargo, podrá especificar una lista de parámetros para la propiedad. Esto es útil para implementar propiedades indizadas o con parámetros de alguna otra manera. Los parámetros siempre se situará en primer lugar, seguido por el nuevo valor para la propiedad. Por ejemplo:  
  
```  
DISP_PROPERTY_PARAM(CMyObject, "item",
    GetItem,
    SetItem,
    VT_DISPATCH,
    VTS_I2 VTS_I2)  
```  
  
 corresponde para obtener y establecer las funciones miembro:  
  
```  
LPDISPATCH CMyObject::GetItem(short row,
    short col)  
void CMyObject::SetItem(short row,
    short col,
    LPDISPATCH newValue)  
```  
  
## <a name="dispxxxxid--macro-descriptions"></a>DISP_XXXX_ID: Descripciones de macros  
  
```  
 
    DISP_FUNCTION_ID(
 theClass,   
    pszName, 
    dispid, 
    pfnMember, 
    vtRetVal, 
    vtsParams)DISP_PROPERTY_ID(
 theClass,   
    pszName, 
    dispid, 
    memberName, 
    vtPropType)DISP_PROPERTY_NOTIFY_ID(
 theClass,   
    pszName, 
    dispid, 
    memberName, 
    pfnAfterSet, 
    vtPropType)DISP_PROPERTY_EX_ID(
 theClass,   
    pszName, 
    dispid, 
    pfnGet, 
    pfnSet, 
    vtPropType)DISP_PROPERTY_PARAM_ID(
 theClass,   
    pszName, 
    dispid, 
    pfnGet, 
    pfnSet, 
    vtPropType, 
    vtsParams) 
```  
  
## <a name="remarks"></a>Comentarios  
  
### <a name="parameters"></a>Parámetros  
 *theClass*  
 Nombre de la clase.  
  
 *pszName*  
 Nombre externo de la propiedad.  
  
 *DISPID*  
 El identificador DISPID fijo para la propiedad o método.  
  
 *pfnGet*  
 Nombre de la función de miembro que se utiliza para obtener la propiedad.  
  
 *pfnSet*  
 Nombre de la función de miembro que se usa para establecer la propiedad.  
  
 *nombre de usuario registrado*  
 El nombre de la variable de miembro para asignar a la propiedad  
  
 *vtPropType*  
 Valor que especifica el tipo de propiedad.  
  
 *vtsParams*  
 Una cadena de espacio separados VTS_ para cada parámetro.  
  
## <a name="remarks"></a>Comentarios  
 Estas macros permiten especificar un **DISPID** en lugar de dejar que MFC automáticamente asignar uno. Estas macros de avanzadas tienen los mismos nombres pero ese identificador se anexa al nombre de la macro (p. ej. **DISP_PROPERTY_ID**) y el identificador se determina mediante el parámetro especificado justo después del *pszName* parámetro. Vea AFXDISP. H para obtener más información sobre estas macros. El **_ID** entradas deben colocarse al final del mapa de envíos. Afecten a automático **DISPID** generación de la misma manera que no **_ID** ¿versión de la macro (la **DISPID**s se determinan por posición). Por ejemplo:  
  
```  
BEGIN_DISPATCH_MAP(CDisp3DPoint,
    CCmdTarget)  
    DISP_PROPERTY(CDisp3DPoint, "y",
    m_y,
    VT_I2)  
    DISP_PROPERTY(CDisp3DPoint, "z",
    m_z,
    VT_I2)  
    DISP_PROPERTY_ID(CDisp3DPoint, "x",
    0x00020003,
    m_x,
    VT_I2)  
END_DISPATCH_MAP()  
```  
  
 MFC generará envío (DISPID) para la clase CDisp3DPoint como se indica a continuación:  
  
```  
property X    (DISPID)0x00020003  
property Y    (DISPID)0x00000002  
property Z     (DISPID)0x00000001  
```  
  
 Especificar un fijo **DISPID** es útil para mantener la compatibilidad con versiones anteriores a una interfaz de envío existentes, o para implementar ciertas propiedades o métodos definidos por el sistema (suele indicar mediante negativo  **DISPID**, como el **DISPID_NEWENUM** colección).  
  
#### <a name="retrieving-the-idispatch-interface-for-a-coleclientitem"></a>Recuperar la interfaz IDispatch de un COleClientItem  
 Muchos servidores será compatible con automatización dentro de sus objetos de documento, junto con la funcionalidad de servidor OLE. Para obtener acceso a esta interfaz de automatización, es necesario tener acceso directamente el `COleClientItem::m_lpObject` variable miembro. El código siguiente recuperará el `IDispatch` para un objeto derivado de la interfaz `COleClientItem`. Puede incluir el código siguiente en la aplicación si se encuentra esta funcionalidad es necesario:  
  
```  
LPDISPATCH CMyClientItem::GetIDispatch()  
{  
    ASSERT_VALID(this);

 ASSERT(m_lpObject != NULL);

 
    LPUNKNOWN lpUnk = m_lpObject;  
 
    Run();
*// must be running  
 
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
    if (lpUnk->QueryInterface(IID_IDispatch, &lpDispatch)   
 != NOERROR)  
 {  
    TRACE0("Warning: does not support IDispatch!\n");

    return NULL;  
 }  
 
    ASSERT(lpDispatch != NULL);

    return lpDispatch;  
}  
```  
  
 La interfaz de envío devuelto de esta función, a continuación, se pueden usar directamente o conectada a un `COleDispatchDriver` para el acceso de seguridad de tipos. Si se usa directamente, asegúrese de que se llama a su `Release` miembro cuando a través con el puntero (el `COleDispatchDriver` destructor hace esto de forma predeterminada).  
  
## <a name="see-also"></a>Vea también  
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)

