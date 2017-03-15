---
title: "TN064: Subprocesamiento de modelo apartamento en los controles ActiveX | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.controls.activex"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "subproceso de modelo de apartamento"
  - "contenedores [C++], con subprocesamiento múltiple"
  - "contenedor multiproceso"
  - "controles OLE, compatibilidad con el contenedor"
  - "TN064"
ms.assetid: b2ab4c88-6954-48e2-9a74-01d4a60df073
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# TN064: Subprocesamiento de modelo apartamento en los controles ActiveX
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea.  Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos.  Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.  
  
 Esta nota técnica se explica cómo habilitar el subprocesamiento de apartamento\- modelo en un control ActiveX.  Observe que los subprocesos de apartamento\- modelo está solo se admite en las versiones de Visual C\+\+ 4,2 o posterior.  
  
## ¿Cuál es el de Apartamento\- modelo?  
 El modelo de apartamento es un enfoque para admitir objetos incrustados, como controles ActiveX, dentro de una aplicación contenedora multiproceso.  Aunque la aplicación puede tener varios subprocesos, cada instancia de un objeto incrustado se asignará a un “apartamento,” que se ejecutará en un solo subproceso.  Es decir todas las llamadas en una instancia de un control sucederán en el mismo subproceso.  
  
 Sin embargo, varias instancias del mismo tipo de control se pueden asignar a apartamentos diferentes.  Por lo tanto, si varias instancias de un control comparten los datos en común \(por ejemplo, datos estáticos o globales\), entonces acceso a this los datos compartidos deberán ser protegidos por un objeto de sincronización, como una sección crítica.  
  
 Para obtener información detallada en el modelo de subprocesos controlados vea [Procesos y subprocesos](http://msdn.microsoft.com/library/windows/desktop/ms684841) en *la referencia\) del Programador*.  
  
## ¿Por qué admite el subprocesamiento de Apartamento\- modelo?  
 Controles que el subprocesamiento admiten el apartamento\- modelo se puede utilizar en las aplicaciones contenedoras multiproceso que también admiten el modelo apartamento.  Si no habilita el subprocesamiento de apartamento\- modelo, limitará el posible conjunto de contenedores en los que el control pueda usar.  
  
 Habilitar el subprocesamiento de apartamento\- modelo es fácil para la mayoría de los controles, especialmente si tienen poco o nada de datos compartidos.  
  
## Proteger los datos compartidos  
 Si el control utiliza datos compartidos, como una variable miembro static, acceso a esos datos se deben proteger con una sección crítica para evitar que más de un subproceso modifica los datos al mismo tiempo.  Para configurar una sección crítica con este fin, declare una variable miembro static de la clase `CCriticalSection` en la clase del control.  Use las funciones miembro de `Lock` y de **Desbloquear** de este objeto de sección crítica siempre que el código tenga acceso a los datos compartidos.  
  
 Considere, por ejemplo, una clase de control necesario mantener una cadena que es compartida por todas las instancias.  Esta cadena se puede mantener en una variable miembro static y proteger por una sección crítica.  La declaración de clase de control contendría el siguiente:  
  
```  
class CSampleCtrl : public COleControl  
{  
    ...  
    static CString _strShared;  
    static CCriticalSection _critSect;  
};  
```  
  
 La implementación de la clase incluiría las definiciones de estas variables:  
  
```  
int CString CSampleCtrl::_strShared;  
CCriticalSection CSampleCtrl::_critSect;  
```  
  
 Acceso al miembro estático de `_strShared` podrá proteger por la sección crítica:  
  
```  
void CSampleCtrl::SomeMethod()  
{  
    _critSect.Lock();  
    if (_strShared.Empty())  
        _strShared = "<text>";  
    _critSect.Unlock();  
    ...  
}  
```  
  
## Registrar un Control de Apartamento\- modelo \- Aware  
 Controles que el subprocesamiento admiten el apartamento\- modelo debe indicar esta capacidad en el registro, agregando el valor denominado “ThreadingModel” con un valor “Apartment” en la entrada de Registro del identificador de la clase en la clave de**InprocServer32** de id\\ *de la clase*.  Para que esta clave automáticamente que se registrará para el control, pase el indicador de `afxRegApartmentThreading` en el sexto parámetro a `AfxOleRegisterControlClass`:  
  
```  
BOOL CSampleCtrl::CSampleCtrlFactory::UpdateRegistry(BOOL bRegister)  
{  
    if (bRegister)  
        return AfxOleRegisterControlClass(  
            AfxGetInstanceHandle(),  
            m_clsid,  
            m_lpszProgID,  
            IDS_SAMPLE,  
            IDB_SAMPLE,  
            afxRegApartmentThreading,  
            _dwSampleOleMisc,  
            _tlid,  
            _wVerMajor,  
            _wVerMinor);  
    else  
        return AfxOleUnregisterClass(m_clsid, m_lpszProgID);  
}  
```  
  
 Si el proyecto de control fue generado por ControlWizard en la versión de Visual C\+\+ 4,1 o posterior, este marcador ya estará presente en el código.  No es necesario ningún cambio registrar el modelo de subprocesos.  
  
 Si el proyecto se ha generado por una versión anterior de ControlWizard, el código existente tendrá un valor boolean como el sexto parámetro.  Si el parámetro existente es TRUE, cambiar a `afxRegInsertable | afxRegApartmentThreading`.  Si el parámetro existente es FALSE, cambiar a `afxRegApartmentThreading`.  
  
 Si el control no sigue las reglas para los subprocesos de apartamento\- modelo, no se debe pasar `afxRegApartmentThreading` en este parámetro.  
  
## Vea también  
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)