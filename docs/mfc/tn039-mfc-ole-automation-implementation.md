---
title: "TN039: Implementaci&#243;n de la automatizaci&#243;n MFC/OLE | Microsoft Docs"
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
  - "vc.mfc.ole"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "automatización, puntos de entrada de la interfaz MFC (COM)"
  - "IDispatch (interfaz)"
  - "MFC, compatibilidad con COM"
  - "MFC, OLE DB y"
  - "TN039"
ms.assetid: 765fa3e9-dd54-4f08-9ad2-26e0546ff8b6
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN039: Implementaci&#243;n de la automatizaci&#243;n MFC/OLE
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea.  Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos.  Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.  
  
## Información general de la interfaz OLE IDispatch  
 La interfaz de `IDispatch` es el medio que aplicaciones exponen métodos y propiedades de que otras aplicaciones como Visual Basic, u otros lenguajes, pueden hacer uso de las características de aplicación.  La parte más importante de esta interfaz es la función de **IDispatch::Invoke** .  MFC utiliza “envío asigna” para implementar **IDispatch::Invoke**.  El mapa de envío proporciona información de implementación de MFC en el diseño o “forma” de `CCmdTarget`\- clases derivadas, de modo que puede manipular directamente las propiedades del objeto, o llamar a funciones miembro dentro del objeto para satisfacer las solicitudes de **IDispatch::Invoke** .  
  
 En general, ClassWizard y MFC cooperan para ocultar la mayoría de los detalles de la automatización OLE del programador de la aplicación.  El programador se concentra en la funcionalidad real para exponer en la aplicación y no tiene que preocuparse de la instalación subyacente.  
  
 Hay casos, sin embargo, donde es necesario conocer lo que hace MFC en segundo plano.  Esta nota se aborda cómo funciona s para **DISPID**de las asignaciones de marco miembro y las propiedades.  Conocer el algoritmo MFC utiliza para asignar s para **DISPID**solo es necesario cuando necesite conocer los id., como cuando se crea una “biblioteca de tipos” para los objetos de la aplicación.  
  
## Asignación de MFC DISPID  
 Aunque el usuario final de automatización \(usuario en Visual Basic, por ejemplo\), considere los nombres reales de las propiedades enabled de automatización y los métodos del código \(como obj.ShowWindow\), la implementación de **IDispatch::Invoke** no recibe los nombres reales.  Por razones de optimización, recibe **DISPID**, que es una “cookie mágica de 32 bits” que describe el método o la propiedad que va a tener acceso.  Estos valores de **DISPID** se devuelven de la implementación de `IDispatch` con otro método, denominado **IDispatch::GetIDsOfNames**.  Una aplicación cliente de automatización llamará `GetIDsOfNames` una vez para cada miembro o propiedad que pretende tener acceso, y los almacena en memoria caché para las llamadas posteriores a **IDispatch::Invoke**.  De esta manera, la búsqueda costosa de la cadena se hace una sola vez por uso de objeto, en lugar de una vez por la llamada de **IDispatch::Invoke** .  
  
 MFC determina s para **DISPID**para cada método y propiedad basados en dos cosas:  
  
-   La distancia desde la parte superior del envío asignar \(1 relativa\)  
  
-   La distancia de envío asignado de la clase derivada \(0 parientes\)  
  
 **DISPID** Se divide en dos partes.  **LOWORD** de **DISPID** contiene el primer componente, la distancia desde la parte superior del mapa de envío.  **HIWORD** contiene la distancia de la clase derivada.  Por ejemplo:  
  
```  
class CDispPoint : public CCmdTarget  
{  
public:  
    short m_x, m_y;  
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
  
BEGIN_DISPATCH_MAP(CDispPoint, CCmdTarget)  
    DISP_PROPERTY(CDispPoint, "x", m_x, VT_I2)  
    DISP_PROPERTY(CDispPoint, "y", m_y, VT_I2)  
END_DISPATCH_MAP()  
  
BEGIN_DISPATCH_MAP(CDisp3DPoint, CDispPoint)  
    DISP_PROPERTY(CDisp3DPoint, "z", m_z, VT_I2)  
END_DISPATCH_MAP()  
```  
  
 Como puede ver, hay dos clases, que expongan interfaces de automatización OLE.  Una de estas clases se derivan de otra y aprovecha así la funcionalidad de la clase base, incluidos la parte de automatización OLE \(propiedades “x” y “y” en este caso\).  
  
 MFC generará s para **DISPID**para la clase CDispPoint como sigue:  
  
```  
property X    (DISPID)0x00000001  
property Y    (DISPID)0x00000002  
```  
  
 Dado que las propiedades no están en una clase base, **HIWORD** de **DISPID** siempre es cero \(la distancia de la clase derivada para CDispPoint es cero\).  
  
 MFC generará s para **DISPID**para la clase CDisp3DPoint como sigue:  
  
```  
property Z    (DISPID)0x00000001  
property X    (DISPID)0x00010001  
property Y    (DISPID)0x00010002  
```  
  
 La propiedad de la z se da **DISPID** con **HIWORD** cero como se define en la clase que se expone las propiedades, CDisp3DPoint.  En las propiedades de X e y se definen en una clase base, **HIWORD** de **DISPID** es 1, ya que la clase en la que se definen estas propiedades está en una distancia de una derivación de la clase derivada.  
  
> [!NOTE]
>  **LOWORD** es particularmente siempre por posición en el mapa, aunque existan las entradas del mapa con **DISPID** explícito \(vea la siguiente sección para obtener información sobre las versiones de **\_ID** macros de `DISP_PROPERTY` y de `DISP_FUNCTION` \).  
  
## Características avanzadas de mapa de envío MFC  
 Hay varias características adicionales que Pero no admite en esta versión de Visual C\+\+.  ClassWizard admite `DISP_FUNCTION`, `DISP_PROPERTY`, y `DISP_PROPERTY_EX` que definen un método, propiedad de variable miembro, y obtiene y establece la propiedad de la función miembro, respectivamente.  Estas funciones son normalmente todas necesarios crear a la mayoría de los servidores de automatización.  
  
 Las macros adicionales siguientes se pueden utilizar cuando las macros compatibles Pero no son adecuadas: `DISP_PROPERTY_NOTIFY`, y `DISP_PROPERTY_PARAM`.  
  
## DISP\_PROPERTY\_NOTIFY — Descripción de macro  
  
```  
  
        DISP_PROPERTY_NOTIFY(   
   theClass,   
   pszName,   
   memberName,   
   pfnAfterSet,   
   vtPropType   
)  
```  
  
## Comentarios  
  
### Parámetros  
 `theClass`  
 Nombre de la clase.  
  
 `pszName`  
 Nombre externo de la propiedad.  
  
 `memberName`  
 Nombre de la variable miembro donde se almacena la propiedad.  
  
 `pfnAfterSet`  
 Nombre de la función miembro que se llama cuando se cambia la propiedad.  
  
 `vtPropType`  
 Un valor que especifica el tipo de propiedad.  
  
## Comentarios  
 Esta macro es la `DISP_PROPERTY`, salvo que acepta un argumento adicional.  El argumento adicional, *pfnAfterSet,* debe ser una función miembro que no devuelve nada y no toma ningún parámetro, “OnPropertyNotify\(\) vacío”.  Se llama **después de que** se ha modificado la variable miembro.  
  
## DISP\_PROPERTY\_PARAM — Descripción de macro  
  
```  
  
        DISP_PROPERTY_PARAM(   
   theClass,  
   pszName,  
   pfnGet,  
   pfnSet,  
   vtPropType,  
   vtsParams   
)  
```  
  
## Comentarios  
  
### Parámetros  
 `theClass`  
 Nombre de la clase.  
  
 `pszName`  
 Nombre externo de la propiedad.  
  
 `memberGet`  
 Nombre de la función miembro utilizada para obtener la propiedad.  
  
 `memberSet`  
 El nombre de la función miembro estableciendo la propiedad.  
  
 `vtPropType`  
 Un valor que especifica el tipo de propiedad.  
  
 `vtsParams`  
 Una cadena de espacio separó VTS\_ para cada parámetro.  
  
## Comentarios  
 Como la macro de `DISP_PROPERTY_EX` , esta macro define una propiedad acceso con independiente get y set funciones miembro.  Esta macro, sin embargo, permite especificar una lista de parámetros para la propiedad.  Esto es útil para implementar propiedades que se indizan o se parametrizan de alguna otra manera.  Los parámetros se colocarán siempre primero, seguido por el nuevo valor de la propiedad.  Por ejemplo:  
  
```  
DISP_PROPERTY_PARAM(CMyObject, "item", GetItem, SetItem, VT_DISPATCH,    VTS_I2 VTS_I2)  
```  
  
 correspondería para obtener y establecer funciones miembro:  
  
```  
LPDISPATCH CMyObject::GetItem(short row, short col)  
void CMyObject::SetItem(short row, short col, LPDISPATCH newValue)  
```  
  
## DISP\_XXXX\_ID — descripciones de macro  
  
```  
  
        DISP_FUNCTION_ID(   
   theClass,  
   pszName,  
   dispid,  
   pfnMember,  
   vtRetVal,  
   vtsParams   
) DISP_PROPERTY_ID(   
   theClass,  
   pszName,  
   dispid,  
   memberName,  
   vtPropType   
) DISP_PROPERTY_NOTIFY_ID(   
   theClass,  
   pszName,  
   dispid,  
   memberName,  
   pfnAfterSet,  
   vtPropType   
) DISP_PROPERTY_EX_ID(   
   theClass,  
   pszName,  
   dispid,  
   pfnGet,  
   pfnSet,  
   vtPropType   
) DISP_PROPERTY_PARAM_ID(   
   theClass,  
   pszName,  
   dispid,  
   pfnGet,  
   pfnSet,  
   vtPropType,  
   vtsParams   
)  
```  
  
## Comentarios  
  
### Parámetros  
 `theClass`  
 Nombre de la clase.  
  
 `pszName`  
 Nombre externo de la propiedad.  
  
 `dispid`  
 El identificador de envío fijo para la propiedad o el método.  
  
 `pfnGet`  
 Nombre de la función miembro utilizada para obtener la propiedad.  
  
 `pfnSet`  
 El nombre de la función miembro estableciendo la propiedad.  
  
 `memberName`  
 El nombre de la variable miembro a asignar a la propiedad  
  
 `vtPropType`  
 Un valor que especifica el tipo de propiedad.  
  
 `vtsParams`  
 Una cadena de espacio separó VTS\_ para cada parámetro.  
  
## Comentarios  
 Estas macros permiten especificar **DISPID** en lugar de permitir que MFC asignar automáticamente uno.  Estas macros avanzados tienen los mismos nombres salvo que el identificador se anexa al nombre de la macro \(por ejemplo.  **DISP\_PROPERTY\_ID**\) y el identificador está determinado por el parámetro especificado justo después del parámetro de `pszName` .  Vea AFXDISP.H para obtener más información sobre estas macros.  Las entradas de **\_ID** se deben colocar al final del mapa de envío.  Afectarán a la generación automática de **DISPID** de la misma manera que una versión que no es de**\_ID** de la macro \(s de **DISPID**viene determinada por la posición\).  Por ejemplo:  
  
```  
BEGIN_DISPATCH_MAP(CDisp3DPoint, CCmdTarget)  
    DISP_PROPERTY(CDisp3DPoint, "y", m_y, VT_I2)  
    DISP_PROPERTY(CDisp3DPoint, "z", m_z, VT_I2)  
    DISP_PROPERTY_ID(CDisp3DPoint, "x", 0x00020003, m_x, VT_I2)  
END_DISPATCH_MAP()  
```  
  
 MFC generará Dispid para la clase CDisp3DPoint como sigue:  
  
```  
property X    (DISPID)0x00020003  
property Y    (DISPID)0x00000002  
property Z     (DISPID)0x00000001  
```  
  
 Especificar **DISPID** fijo es útil para mantener la compatibilidad con versiones anteriores a una interfaz de envío previamente existente, o al implementar un sistema definido métodos o propiedades \(se indica normalmente por **DISPID**negativo, como la colección de **DISPID\_NEWENUM** \).  
  
#### Recuperar la interfaz IDispatch para un COleClientItem  
 Muchos servidores admitirán automatización dentro de los objetos document, junto con la funcionalidad de servidor OLE.  Para obtener acceso a esta interfaz de automatización, es necesario tener acceso directamente a la variable miembro de **COleClientItem::m\_lpObject** .  El código siguiente recuperará la interfaz de `IDispatch` para un objeto derivado de `COleClientItem`.  Puede incluir el código siguiente en la aplicación si detecta esta funcionalidad necesaria:  
  
```  
LPDISPATCH CMyClientItem::GetIDispatch()  
{  
    ASSERT_VALID(this);  
    ASSERT(m_lpObject != NULL);  
  
    LPUNKNOWN lpUnk = m_lpObject;  
  
    Run();    // must be running  
  
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
  
 La interfaz de envío devuelta por esta función se podría utilizar directamente o adjuntar a `COleDispatchDriver` para el acceso tipo\- seguro.  Si se utiliza directamente, asegúrese de llamar a su miembro de **Versión** cuando a través con de puntero \( `COleDispatchDriver` destructor hace de forma predeterminada\).  
  
## Vea también  
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)