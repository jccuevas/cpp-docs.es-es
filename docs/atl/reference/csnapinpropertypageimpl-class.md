---
title: Clase CSnapInPropertyPageImpl | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSnapInPropertyPageImpl
- ATLSNAP/ATL::CSnapInPropertyPageImpl
- ATLSNAP/ATL::CSnapInPropertyPageImpl::CSnapInPropertyPageImpl
- ATLSNAP/ATL::CSnapInPropertyPageImpl::CancelToClose
- ATLSNAP/ATL::CSnapInPropertyPageImpl::Create
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnApply
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnHelp
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnKillActive
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnQueryCancel
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnReset
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnSetActive
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnWizardBack
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnWizardFinish
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnWizardNext
- ATLSNAP/ATL::CSnapInPropertyPageImpl::QuerySiblings
- ATLSNAP/ATL::CSnapInPropertyPageImpl::SetModified
- ATLSNAP/ATL::CSnapInPropertyPageImpl::m_psp
dev_langs:
- C++
helpviewer_keywords:
- snap-ins, property pages
- snap-ins
- property pages, ATL
- CSnapInPropertyPageImpl class
ms.assetid: 75bdce5a-985e-4166-bd44-493132e023c4
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: f5db4d0742a423e9574db2a4268a9376491b2ed2
ms.lasthandoff: 02/24/2017

---
# <a name="csnapinpropertypageimpl-class"></a>Clase CSnapInPropertyPageImpl
Esta clase proporciona métodos para implementar un objeto de página de propiedades del complemento.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no pueden utilizarse en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
CSnapInPropertyPageImpl : public CDialogImplBase
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CSnapInPropertyPageImpl::CSnapInPropertyPageImpl](#csnapinpropertypageimpl)|Constructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CSnapInPropertyPageImpl::CancelToClose](#canceltoclose)|Cambia el estado de la **Aceptar** y **cancelar** botones.|  
|[CSnapInPropertyPageImpl::Create](#create)|Inicializa un recién creado `CSnapInPropertyPageImpl` objeto.|  
|[CSnapInPropertyPageImpl::OnApply](#onapply)|Llamado por el marco de trabajo cuando el usuario hace clic en el **aplicar ahora** botón mientras utiliza una hoja de propiedades del tipo de asistente.|  
|[CSnapInPropertyPageImpl::OnHelp](#onhelp)|Llamado por el marco de trabajo cuando el usuario hace clic en el **ayuda** botón mientras utiliza una hoja de propiedades del tipo de asistente.|  
|[CSnapInPropertyPageImpl::OnKillActive](#onkillactive)|Llamado por el marco de trabajo cuando la página actual ya no está activa.|  
|[CSnapInPropertyPageImpl::OnQueryCancel](#onquerycancel)|Llamado por el marco de trabajo cuando el usuario hace clic en el **cancelar** botón y antes de que la cancelación tenga lugar.|  
|[CSnapInPropertyPageImpl::OnReset](#onreset)|Llamado por el marco de trabajo cuando el usuario hace clic en el **restablecer** botón mientras utiliza una hoja de propiedades del tipo de asistente.|  
|[CSnapInPropertyPageImpl::OnSetActive](#onsetactive)|Lo llama el marco de trabajo cuando se activa la página actual.|  
|[CSnapInPropertyPageImpl::OnWizardBack](#onwizardback)|Llamado por el marco de trabajo cuando el usuario hace clic en el **Atrás** botón mientras utiliza una hoja de propiedades del tipo de asistente.|  
|[CSnapInPropertyPageImpl::OnWizardFinish](#onwizardfinish)|Llamado por el marco de trabajo cuando el usuario hace clic en el **finalizar** botón mientras utiliza una hoja de propiedades del tipo de asistente.|  
|[CSnapInPropertyPageImpl::OnWizardNext](#onwizardnext)|Llamado por el marco de trabajo cuando el usuario hace clic en el `Next` botón mientras utiliza una hoja de propiedades del tipo de asistente.|  
|[CSnapInPropertyPageImpl::QuerySiblings](#querysiblings)|Reenvía el mensaje actual para todas las páginas de la hoja de propiedades.|  
|[CSnapInPropertyPageImpl::SetModified](#setmodified)|Llamada a activar o desactivar el **aplicar ahora** botón.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CSnapInPropertyPageImpl::m_psp](#m_psp)|Windows **PROPSHEETPAGE** estructura utilizada por la `CSnapInPropertyPageImpl` objeto.|  
  
## <a name="remarks"></a>Comentarios  
 `CSnapInPropertyPageImpl`Proporciona una implementación básica de un objeto de página de propiedades del complemento. Las características básicas de una página de propiedades del complemento se implementan mediante varias interfaces distintas y asignan los tipos.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `CDialogImplBase`  
  
 `CSnapInPropertyPageImpl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlsnap.h  
  
##  <a name="canceltoclose"></a>CSnapInPropertyPageImpl::CancelToClose  
 Llame a esta función una vez que se ha realizado un cambio irrecuperable a los datos en una página de una hoja de propiedades modales.  
  
```
void CancelToClose();
```  
  
### <a name="remarks"></a>Comentarios  
 Esta función se cambiará la **Aceptar** botón a **cerrar** y deshabilitar la **cancelar** botón. Esto cambia el usuario que un cambio es permanente y las modificaciones no se puede cancelar las alertas.  
  
 El `CancelToClose` función miembro no hace nada en una hoja de propiedades no modales, porque no tiene una hoja de propiedades no modal un **cancelar** botón de forma predeterminada.  
  
##  <a name="csnapinpropertypageimpl"></a>CSnapInPropertyPageImpl::CSnapInPropertyPageImpl  
 Construye un objeto `CSnapInPropertyPageImpl`.  
  
```
CSnapInPropertyPageImpl(LPCTSTR lpszTitle = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszTitle`  
 [in] El título de la página de propiedades.  
  
### <a name="remarks"></a>Comentarios  
 Para inicializar la estructura subyacente, llame a [CSnapInPropertyPageImpl::Create](#create).  
  
##  <a name="create"></a>CSnapInPropertyPageImpl::Create  
 Llame a esta función para inicializar la estructura subyacente de la página de propiedades.  
  
```
HPROPSHEETPAGE Create();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un identificador de un **PROPSHEETPAGE** estructura que contiene los atributos de la hoja de propiedades recién creada.  
  
### <a name="remarks"></a>Comentarios  
 Debe llamar primero a [CSnapInPropertyPageImpl::CSnapInPropertyPageImpl](#csnapinpropertypageimpl) antes de llamar a esta función.  
  
##  <a name="m_psp"></a>CSnapInPropertyPageImpl::m_psp  
 `m_psp`es una estructura cuyos miembros almacenan las características de **PROPSHEETPAGE**.  
  
```
PROPSHEETPAGE m_psp;
```  
  
### <a name="remarks"></a>Comentarios  
 Utilice esta estructura para inicializar la apariencia de una página de propiedades después de construirlo.  
  
 Para obtener más información sobre esta estructura, incluida una lista de sus miembros, vea [PROPSHEETPAGE](http://msdn.microsoft.com/library/aa815151) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="onapply"></a>CSnapInPropertyPageImpl::OnApply  
 Esta función miembro se llama cuando el usuario hace clic en el **Aceptar** o **aplicar ahora** botón.  
  
```
BOOL OnApply();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se aceptan los cambios; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Antes de `OnApply` se puede llamar mediante el marco de trabajo, debe haber llamado `SetModified` y establecer su parámetro **TRUE**. Esto activará la **aplicar ahora** botón tan pronto como el usuario realiza un cambio en la página de propiedades.  
  
 Reemplace esta función miembro para especificar qué acción el programa realiza cuando el usuario hace clic en el **aplicar ahora** botón. Cuando se reemplaza, la función debe devolver **TRUE** para aceptar los cambios y **FALSE** para evitar que los cambios surten efecto.  
  
 La implementación predeterminada de `OnApply` devuelve **TRUE**.  
  
##  <a name="onhelp"></a>CSnapInPropertyPageImpl::OnHelp  
 Esta función miembro se llama cuando el usuario hace clic en el **ayuda** botón de la página de propiedades.  
  
```
void OnHelp();
```  
  
### <a name="remarks"></a>Comentarios  
 Reemplace esta función miembro para mostrar la Ayuda de la página de propiedades.  
  
##  <a name="onkillactive"></a>CSnapInPropertyPageImpl::OnKillActive  
 Esta función miembro se llama cuando la página ya no es la página activa.  
  
```
BOOL OnKillActive();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si los datos se actualizan correctamente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Reemplace esta función miembro para llevar a cabo las tareas de validación de datos especiales.  
  
##  <a name="onquerycancel"></a>CSnapInPropertyPageImpl::OnQueryCancel  
 Esta función miembro se llama cuando el usuario hace clic en el **cancelar** botón y antes de cancelar la acción ha tenido lugar.  
  
```
BOOL OnQueryCancel();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero para permitir que la operación de cancelación; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Reemplace esta función miembro para especificar una acción realizada por el programa cuando el usuario hace clic en el **cancelar** botón.  
  
 La implementación predeterminada de `OnQueryCancel` devuelve **TRUE**.  
  
##  <a name="onreset"></a>CSnapInPropertyPageImpl::OnReset  
 Esta función miembro se llama cuando el usuario hace clic en el **cancelar** botón.  
  
```
void OnReset();
```  
  
### <a name="remarks"></a>Comentarios  
 Cuando se llama a esta función, se cambia a todas las páginas de propiedad realizados por el usuario anteriormente al hacer clic en el **aplicar ahora** botón se descartan y la hoja de propiedades conserva el foco.  
  
 Reemplace esta función miembro para especificar qué acción el programa realiza cuando el usuario hace clic en el **cancelar** botón.  
  
##  <a name="onsetactive"></a>CSnapInPropertyPageImpl::OnSetActive  
 Esta función miembro se llama cuando la página se ha elegido por el usuario y se convierte en la página activa.  
  
```
BOOL OnSetActive();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la página se estableció correctamente activa; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Reemplace esta función miembro para realizar tareas cuando se activa una página. La invalidación de esta función miembro debe llamar a la versión predeterminada antes de realiza cualquier otro procesamiento.  
  
 La implementación predeterminada devuelve **TRUE**.  
  
##  <a name="onwizardback"></a>CSnapInPropertyPageImpl::OnWizardBack  
 Esta función miembro se llama cuando el usuario hace clic en el **Atrás** botón en un asistente.  
  
```
BOOL OnWizardBack();
```  
  
### <a name="return-value"></a>Valor devuelto  
  
-   0 para avanzar automáticamente a la página anterior.  
  
-   -1 para evitar que la página cambie.  
  
 Para saltar a una página distinta de la siguiente, devolver el identificador del cuadro de diálogo que aparecerá.  
  
### <a name="remarks"></a>Comentarios  
 Reemplace esta función miembro para especificar una acción que debe realizar cuando el usuario la **vuelva** se hace clic en el botón.  
  
##  <a name="onwizardfinish"></a>CSnapInPropertyPageImpl::OnWizardFinish  
 Esta función miembro se llama cuando el usuario hace clic en el **finalizar** botón en un asistente.  
  
```
BOOL OnWizardFinish();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la hoja de propiedades se destruye cuando finalice el Asistente; en caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Reemplace esta función miembro para especificar una acción que debe realizar cuando el usuario la **finalizar** se hace clic en el botón.  
  
##  <a name="onwizardnext"></a>CSnapInPropertyPageImpl::OnWizardNext  
 Esta función miembro se llama cuando el usuario hace clic en el `Next` botón en un asistente.  
  
```
BOOL OnWizardNext();
```  
  
### <a name="return-value"></a>Valor devuelto  
  
-   de&0; a avanza automáticamente a la página siguiente.  
  
-   -1 para evitar que la página cambie.  
  
 Para saltar a una página distinta de la siguiente, devolver el identificador del cuadro de diálogo que aparecerá.  
  
### <a name="remarks"></a>Comentarios  
 Reemplace esta función miembro para especificar una acción que debe realizar cuando el usuario la `Next` se hace clic en el botón.  
  
##  <a name="querysiblings"></a>CSnapInPropertyPageImpl::QuerySiblings  
 Llame a esta función miembro para reenviar un mensaje a cada página de la hoja de propiedades.  
  
```
LRESULT QuerySiblings(WPARAM wParam, LPARAM lParam);
```  
  
### <a name="parameters"></a>Parámetros  
 `wParam`  
 [in] Especifica información adicional de mensaje dependiente.  
  
 `lParam`  
 [in] Especifica información adicional de mensaje dependiente.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si no se debe reenviar el mensaje a la siguiente página de propiedades; en caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Si una página devuelve un valor distinto de cero, la hoja de propiedades no envía el mensaje a las páginas siguientes.  
  
##  <a name="setmodified"></a>CSnapInPropertyPageImpl::SetModified  
 Llame a esta función miembro para habilitar o deshabilitar la **aplicar ahora** botón, en función de si se debe aplicar la configuración en la página de propiedades para el objeto externo adecuado.  
  
```
void SetModified(BOOL bChanged = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `bChanged`  
 [in] **TRUE** para indicar que la configuración de la página de propiedades se han modificado desde la última vez que se aplicaron; **FALSE** para indicar que la configuración de la página de propiedades se han aplicado o debe omitirse.  
  
### <a name="remarks"></a>Comentarios  
 La hoja de propiedades realiza el seguimiento de las páginas son "sucio", es decir, páginas de propiedades para la que ha llamado **SetModified (TRUE)**. El **aplicar ahora** botón siempre estará habilitado si se llama a **SetModified (TRUE)** para una de las páginas. El **aplicar ahora** botón se deshabilitará cuando se llama a **SetModified (FALSE)** para una de las páginas, pero sólo si ninguna de las otras páginas "sucio."  
  
## <a name="see-also"></a>Vea también  
 [Información general de la clase](../../atl/atl-class-overview.md)

