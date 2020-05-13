---
title: 'TN064: Subprocesamiento de modelo apartamento en los controles ActiveX'
ms.date: 11/04/2016
helpviewer_keywords:
- OLE controls [MFC], container support
- containers [MFC], multithreaded
- TN064 [MFC]
- multithread container [MFC]
- apartment model threading [MFC]
ms.assetid: b2ab4c88-6954-48e2-9a74-01d4a60df073
ms.openlocfilehash: 0c6a42124b4b2b03ae7cd9277fa14d43eac7a2bb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366070"
---
# <a name="tn064-apartment-model-threading-in-activex-controls"></a>TN064: Subprocesamiento de modelo apartamento en los controles ActiveX

> [!NOTE]
> La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea. Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos. Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.

Esta nota técnica explica cómo habilitar el subproceso de modelo de apartamento en un control ActiveX. Tenga en cuenta que el subproceso del modelo de apartamento solo se admite en Visual C++ versiones 4.2 o posteriores.

## <a name="what-is-apartment-model-threading"></a>Qué es el subproceso de modelo de apartamento

El modelo de apartamento es un enfoque para admitir objetos incrustados, como controles ActiveX, dentro de una aplicación contenedora multiproceso. Aunque la aplicación puede tener varios subprocesos, cada instancia de un objeto incrustado se asignará a un "apartamento", que se ejecutará en un solo subproceso. En otras palabras, todas las llamadas a una instancia de un control se producirán en el mismo subproceso.

Sin embargo, se pueden asignar diferentes instancias del mismo tipo de control a diferentes apartamentos. Por lo tanto, si varias instancias de un control comparten datos en común (por ejemplo, datos estáticos o globales), el acceso a estos datos compartidos deberá estar protegido por un objeto de sincronización, como una sección crítica.

Para obtener información detallada sobre el modelo de roscado de apartamento, consulte [Procesos y subprocesos](/windows/win32/ProcThread/processes-and-threads) en la *referencia del programador OLE*.

## <a name="why-support-apartment-model-threading"></a>Por qué admitir el subproceso de modelo de apartamento

Los controles que admiten el subproceso del modelo de apartamento se pueden usar en aplicaciones de contenedor multiproceso que también admiten el modelo de apartamento. Si no habilita el subproceso del modelo de apartamento, limitará el conjunto potencial de contenedores en los que se podría usar el control.

Habilitar el subproceso de modelo de apartamento es fácil para la mayoría de los controles, especialmente si tienen pocos o ningún dato compartido.

## <a name="protecting-shared-data"></a>Protección de datos compartidos

Si el control utiliza datos compartidos, como una variable miembro estática, el acceso a esos datos debe protegerse con una sección crítica para evitar que más de un subproceso modifique los datos al mismo tiempo. Para configurar una sección crítica para este propósito, `CCriticalSection` declare una variable miembro estática de clase en la clase del control. Utilice `Lock` las `Unlock` funciones miembro y las de este objeto de sección crítica siempre que el código tenga acceso a los datos compartidos.

Considere, por ejemplo, una clase de control que necesita mantener una cadena compartida por todas las instancias. Esta cadena se puede mantener en una variable miembro estática y protegida por una sección crítica. La declaración de clase del control contendría lo siguiente:

```cpp
class CSampleCtrl : public COleControl
{
...
    static CString _strShared;
    static CCriticalSection _critSect;
};
```

La implementación de la clase incluiría definiciones para estas variables:

```cpp
int CString CSampleCtrl::_strShared;
CCriticalSection CSampleCtrl::_critSect;
```

El acceso `_strShared` al miembro estático puede entonces ser protegido por la sección crítica:

```cpp
void CSampleCtrl::SomeMethod()
{
    _critSect.Lock();
if (_strShared.Empty())
    _strShared = "<text>";
    _critSect.Unlock();

...
}
```

## <a name="registering-an-apartment-model-aware-control"></a>Registro de un control consciente del modelo de apartamentos

Los controles que admiten el subproceso del modelo de apartamento deben indicar esta capacidad en el registro, agregando el valor con nombre "ThreadingModel" con un valor de "Apartment" en su entrada de registro de identificador de clase bajo la clave\\**inprocServer32** de identificador de *clase.* Para hacer que esta clave se registre automáticamente para el control, pase la `AfxOleRegisterControlClass`marca *afxRegApartmentThreading* en el sexto parámetro a:

```cpp
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

Si controlWizard generó el proyecto de control en Visual C++ versión 4.1 o posterior, esta marca ya estará presente en el código. No es necesario realizar cambios para registrar el modelo de subprocesamiento.

Si el proyecto se generó mediante una versión anterior de ControlWizard, el código existente tendrá un valor booleano como sexto parámetro. Si el parámetro existente es TRUE, cámbielo a *afxRegInsertable áfxRegApartmentThreading*. Si el parámetro existente es FALSE, cámbielo a *afxRegApartmentThreading*.

Si el control no sigue las reglas para el subproceso de modelo de apartamento, no debe pasar *afxRegApartmentThreading* en este parámetro.

## <a name="see-also"></a>Consulte también

[Notas técnicas por número](../mfc/technical-notes-by-number.md)<br/>
[Notas técnicas por categoría](../mfc/technical-notes-by-category.md)
