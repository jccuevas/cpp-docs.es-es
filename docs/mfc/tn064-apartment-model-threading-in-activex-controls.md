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
ms.openlocfilehash: f490e82e179da4614eea345136a9edfb1d320705
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442115"
---
# <a name="tn064-apartment-model-threading-in-activex-controls"></a>TN064: Subprocesamiento de modelo apartamento en los controles ActiveX

> [!NOTE]
>  La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea. Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos. Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.

En esta nota técnica se explica cómo habilitar los subprocesos de modelo de apartamento en un control ActiveX. Tenga en cuenta que los subprocesos del modelo de Apartamento C++ solo se admiten en las versiones de Visual 4,2 o posterior.

## <a name="what-is-apartment-model-threading"></a>Qué es el subprocesamiento de modelo de apartamento

El modelo de apartamento es un enfoque para admitir objetos incrustados, como controles ActiveX, dentro de una aplicación contenedora multiproceso. Aunque la aplicación puede tener varios subprocesos, cada instancia de un objeto incrustado se asignará a un "Apartamento", que se ejecutará en un solo subproceso. En otras palabras, todas las llamadas a una instancia de un control se producirán en el mismo subproceso.

Sin embargo, se pueden asignar diferentes instancias del mismo tipo de control a distintos apartamentos. Por lo tanto, si varias instancias de un control comparten datos en común (por ejemplo, datos estáticos o globales), el acceso a estos datos compartidos tendrá que protegerse mediante un objeto de sincronización, como una sección crítica.

Para obtener detalles completos sobre el modelo de subprocesos de apartamento, vea [procesos y subprocesos](/windows/win32/ProcThread/processes-and-threads) en la *Referencia del programador de OLE*.

## <a name="why-support-apartment-model-threading"></a>¿Por qué admitir subprocesos de modelo de apartamento?

Los controles que admiten subprocesos de modelo de apartamento se pueden usar en aplicaciones de contenedor multiproceso que también admiten el modelo de apartamento. Si no habilita el subprocesamiento de modelo apartamento, limitará el conjunto potencial de contenedores en los que se podría usar el control.

La habilitación de subprocesos de modelo apartamento es fácil para la mayoría de los controles, especialmente si tienen pocos o ningún dato compartido.

## <a name="protecting-shared-data"></a>Protección de datos compartidos

Si el control usa datos compartidos, como una variable miembro estática, el acceso a esos datos debe protegerse con una sección crítica para evitar que más de un subproceso modifique los datos al mismo tiempo. Para configurar una sección crítica para este propósito, declare una variable miembro estática de la clase `CCriticalSection` en la clase del control. Use las funciones miembro `Lock` y `Unlock` de este objeto de sección crítica siempre que el código tenga acceso a los datos compartidos.

Considere, por ejemplo, una clase de control que necesita mantener una cadena compartida por todas las instancias. Esta cadena se puede mantener en una variable miembro estática y estar protegida por una sección crítica. La declaración de clase del control incluiría lo siguiente:

```
class CSampleCtrl : public COleControl
{
...
    static CString _strShared;
    static CCriticalSection _critSect;
};
```

La implementación de la clase incluiría definiciones para estas variables:

```
int CString CSampleCtrl::_strShared;
CCriticalSection CSampleCtrl::_critSect;
```

A continuación, la sección crítica puede proteger el acceso al miembro estático `_strShared`:

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

## <a name="registering-an-apartment-model-aware-control"></a>Registrar un control compatible con el modelo de apartamento

Los controles que admiten el subprocesamiento de modelo Apartamento deben indicar esta capacidad en el registro, agregando el valor con nombre "ThreadingModel" con un valor de "Apartment" en su entrada de registro de ID. de clase en el ID. de *clase*\\clave **InProcServer32** . Para que esta clave se registre automáticamente para el control, pase la marca *afxRegApartmentThreading* del sexto parámetro a `AfxOleRegisterControlClass`:

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

Si el proyecto de control lo generó ControlWizard en la C++ versión de Visual 4,1 o posterior, esta marca ya estará presente en el código. No es necesario realizar ningún cambio para registrar el modelo de subprocesos.

Si el proyecto se generó con una versión anterior de ControlWizard, el código existente tendrá un valor booleano como el sexto parámetro. Si el parámetro existente es TRUE, cámbielo a *afxRegInsertable | afxRegApartmentThreading*. Si el parámetro existente es FALSE, cámbielo a *afxRegApartmentThreading*.

Si el control no sigue las reglas de subprocesamiento de modelo apartamento, no debe pasar *afxRegApartmentThreading* en este parámetro.

## <a name="see-also"></a>Consulte también

[Notas técnicas por número](../mfc/technical-notes-by-number.md)<br/>
[Notas técnicas por categoría](../mfc/technical-notes-by-category.md)
