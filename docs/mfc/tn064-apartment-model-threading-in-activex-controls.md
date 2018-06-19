---
title: 'TN064: Subprocesamiento de modelo apartamento en los controles ActiveX | Documentos de Microsoft'
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
ms.openlocfilehash: 515103fc66ad221a3806fc101dcbc01f507ef535
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33383193"
---
# <a name="tn064-apartment-model-threading-in-activex-controls"></a>TN064: Subprocesamiento de modelo apartamento en los controles ActiveX
> [!NOTE]
>  La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea. Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos. Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.  
  
 Esta nota técnica explica cómo habilitar el modelo de subprocesamiento controlado en un control ActiveX. Tenga en cuenta que el modelo de subprocesamiento controlado se admite solo en Visual C++ versión 4.2 o posterior.  
  
## <a name="what-is-apartment-model-threading"></a>¿Qué es el modelo de subprocesamiento controlado  
 El modelo de apartamento es un enfoque para admitir objetos incrustados, como los controles ActiveX, dentro de una aplicación de contenedor multiproceso. Aunque la aplicación puede tener varios subprocesos, cada instancia de un objeto incrustado se asignará a una "apartamento" que se ejecutará en un solo subproceso. En otras palabras, todas las llamadas en una instancia de un control se realizará en el mismo subproceso.  
  
 Sin embargo, diferentes instancias del mismo tipo de control pueden asignarse a contenedores diferentes. Por lo tanto, si varias instancias de un control comparten los datos en común (por ejemplo, los datos globales o estáticos), acceso a los datos compartidos necesitará estén protegidos por un objeto de sincronización, como una sección crítica.  
  
 Para obtener información detallada en el modelo de subprocesamiento controlado, consulte [procesos y subprocesos](http://msdn.microsoft.com/library/windows/desktop/ms684841) en el *referencia del programador de OLE*.  
  
## <a name="why-support-apartment-model-threading"></a>¿Por qué admite el modelo de subprocesamiento controlado  
 Controles que admiten el modelo de subprocesamiento controlado se pueden usar en aplicaciones de contenedor multiproceso que también admiten el modelo de apartamento. Si no habilita el modelo de subprocesamiento controlado, limitará el posible conjunto de contenedores en el que se podría usar el control.  
  
 Habilitar el modelo de subprocesamiento controlado es fácil para la mayoría de los controles, especialmente si tienen poca o ninguna datos compartidos.  
  
## <a name="protecting-shared-data"></a>Proteger los datos compartidos  
 Si el control usa datos compartidos, como una variable miembro estática, el acceso a que los datos deberían estar protegidos con una sección crítica para evitar que más de un subproceso de modificación de los datos al mismo tiempo. Para configurar una sección crítica para este propósito, declare una variable de miembro estático de la clase `CCriticalSection` en la clase del control. Use la `Lock` y **Unlock** las funciones miembro de esta sección crítica de objeto siempre que el código tiene acceso a los datos compartidos.  
  
 Considere, por ejemplo, una clase de control que necesita para mantener una cadena que es compartida por todas las instancias. Esta cadena se puede mantener en una variable de miembro estático y protegida por una sección crítica. Declaración de clase del control podría contener lo siguiente:  
  
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
  
 El acceso a la `_strShared` miembro estático, a continuación, se puede proteger por la sección crítica:  
  
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
  
## <a name="registering-an-apartment-model-aware-control"></a>Cómo registrar un Control contenedor-compatible con el modelo  
 Controles que admiten el modelo de subprocesamiento controlado deben indicar esta capacidad en el registro agregando el valor con nombre "ThreadingModel" con un valor de "Apartamento" en su entrada de registro de Id. de clase en el *Id. de clase* \\ **InprocServer32** clave. Para hacer que esta clave se registre automáticamente para el control, pase el `afxRegApartmentThreading` marca del sexto parámetro para `AfxOleRegisterControlClass`:  
  
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
  
 Si el proyecto de control se generó utilizando ControlWizard en Visual C++ versión 4.1 o posterior, esta marca ya estará presente en el código. No hay cambios son necesarios para registrar el modelo de subprocesos.  
  
 Si el proyecto se generó utilizando una versión anterior de ControlWizard, el código existente tendrá un valor booleano como el sexto parámetro. Si el parámetro existente es TRUE, cámbiela a `afxRegInsertable | afxRegApartmentThreading`. Si el parámetro existente es FALSE, cámbiela a `afxRegApartmentThreading`.  
  
 Si el control no sigue las reglas para el modelo de subprocesamiento controlado, no debe pasar `afxRegApartmentThreading` en este parámetro.  
  
## <a name="see-also"></a>Vea también  
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)

