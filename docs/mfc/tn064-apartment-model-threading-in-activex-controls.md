---
title: 'TN064: Subprocesamiento de modelo apartamento en los controles ActiveX | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.controls.activex
dev_langs:
- C++
helpviewer_keywords:
- OLE controls [MFC], container support
- containers [MFC], multithreaded
- TN064 [MFC]
- multithread container [MFC]
- apartment model threading [MFC]
ms.assetid: b2ab4c88-6954-48e2-9a74-01d4a60df073
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 262760ecc835d9b82dde81bf9d8602f775ad7f50
ms.sourcegitcommit: f7703076b850c717c33d72fb0755fbb2215c5ddc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/28/2018
ms.locfileid: "43131537"
---
# <a name="tn064-apartment-model-threading-in-activex-controls"></a>TN064: Subprocesamiento de modelo apartamento en los controles ActiveX
> [!NOTE]
>  La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea. Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos. Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.  
  
 Esta nota técnica explica cómo habilitar el modelo de subprocesamiento controlado en un control ActiveX. Tenga en cuenta que subprocesamiento de modelo solo se admite en versiones de Visual C++ 4.2 o posteriores.  
  
## <a name="what-is-apartment-model-threading"></a>¿Qué es el modelo de subprocesamiento controlado  
 El modelo de apartamento es un enfoque para aceptar objetos incrustados, como los controles ActiveX, dentro de una aplicación de contenedor multiproceso. Aunque la aplicación puede tener varios subprocesos, cada instancia de un objeto incrustado se asignará a un "contenedor," que se ejecutará en un solo subproceso. En otras palabras, todas las llamadas en una instancia de un control se realizará en el mismo subproceso.  
  
 Sin embargo, se pueden asignar distintas instancias del mismo tipo de control a apartamentos diferentes. Por lo tanto, si varias instancias de un control comparten los datos en común (por ejemplo, los datos globales o estáticos), a continuación, acceso a los datos compartidos deberá estar protegido por un objeto de sincronización, como una sección crítica.  
  
 Para obtener información detallada sobre el modelo de subprocesamiento controlado, consulte [procesos y subprocesos](/windows/desktop/ProcThread/processes-and-threads) en el *referencia del programador OLE*.  
  
## <a name="why-support-apartment-model-threading"></a>¿Por qué admiten subprocesamiento de modelo  
 Los controles que admiten el modelo de subprocesamiento controlado pueden usarse en aplicaciones de contenedor multiproceso que también admiten el modelo de apartamento. Si no habilita el modelo de subprocesamiento controlado, limitará el posible conjunto de contenedores en el que podría utilizarse el control.  
  
 Habilitación de subprocesamiento de modelo es fácil para la mayoría de los controles, especialmente si tienen poca o ninguna datos compartidos.  
  
## <a name="protecting-shared-data"></a>Protección de datos compartido  
 Si el control usa datos compartidos, como una variable de miembro estático, el acceso a que los datos deben estar protegidos con una sección crítica para evitar que más de un subproceso modificando los datos al mismo tiempo. Para configurar una sección crítica para este propósito, declare una variable de miembro estático de la clase `CCriticalSection` en la clase del control. Use la `Lock` y `Unlock` las funciones miembro de esta sección crítica de objeto siempre que el código tiene acceso a los datos compartidos.  
  
 Considere, por ejemplo, una clase de control que necesita para mantener una cadena que es compartida por todas las instancias. Esta cadena puede se mantienen en una variable miembro estática y protegida por una sección crítica. Declaración de clase del control podría contener lo siguiente:  
  
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
  
 El acceso a la `_strShared` miembro estático, a continuación, se puede proteger mediante la sección crítica:  
  
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
  
## <a name="registering-an-apartment-model-aware-control"></a>Registrar un apartamento-compatible con el modelo de Control  
 Los controles que admiten el modelo de subprocesamiento controlado deben indicar esta funcionalidad en el registro, sumando el valor con nombre "ThreadingModel" con un valor de "Contenedor" en su entrada de registro de Id. de clase bajo el *Id. de clase* \\ **InprocServer32** clave. Para hacer que esta clave se registre automáticamente para el control, pase el *afxRegApartmentThreading* marca en el sexto parámetro `AfxOleRegisterControlClass`:  
  
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
    return AfxOleUnregisterClass(m_clsid,
    m_lpszProgID);

}  
```  
  
 Si se ha generado el proyecto de control ControlWizard en Visual C++ versión 4.1 o posterior, esta marca ya estará presente en el código. No hay cambios son necesarios para registrar el modelo de subprocesos.  
  
 Si el proyecto generado por una versión anterior de ControlWizard, el código existente tendrá un valor booleano como el sexto parámetro. Si el parámetro existente es TRUE, cámbiela a *afxRegInsertable | afxRegApartmentThreading*. Si el parámetro existente es FALSE, cámbielo a *afxRegApartmentThreading*.  
  
 Si el control no cumple las reglas de subprocesamiento de modelo, no se debe pasar *afxRegApartmentThreading* en este parámetro.  
  
## <a name="see-also"></a>Vea también  
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)

