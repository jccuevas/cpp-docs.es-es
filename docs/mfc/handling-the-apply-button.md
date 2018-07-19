---
title: Controlar el botón Aplicar | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Apply button in property sheet
- property sheets, Apply button
ms.assetid: 7e977015-59b8-406f-b545-aad0bfd8d55b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: acbbd4ec8e075abbcbbeeaf199cae0d3a8d3c41a
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930457"
---
# <a name="handling-the-apply-button"></a>Controlar el botón Aplicar
Hojas de propiedades tienen una capacidad que no lo hacen de cuadros de diálogo estándar: permiten que el usuario aplicar los cambios que han realizado antes de cerrar la hoja de propiedades. Esto se realiza mediante el botón Aplicar. En este artículo se describe los métodos que puede usar para implementar correctamente esta característica.  
  
 Cuadros de diálogo modales suelen aplican la configuración a un objeto externo cuando el usuario hace clic en Aceptar para cerrar el cuadro de diálogo. Lo mismo puede decirse de una hoja de propiedades: cuando el usuario hace clic en Aceptar, la nueva configuración de la hoja de propiedades surta efecto.  
  
 Sin embargo, puede que desee permitir al usuario guardar la configuración sin tener que cerrar el cuadro de diálogo de la hoja de propiedades. Se trata de la función del botón Aplicar. El botón Aplicar aplica la configuración actual en todas las páginas de propiedades para el objeto externo, en lugar de aplicar sólo la configuración actual de la página activa actualmente.  
  
 De forma predeterminada, el botón Aplicar siempre está deshabilitado. Debe escribir código para habilitar el botón Aplicar en el momento adecuado y se debe escribir código para implementar el efecto de aplicar, como se explica a continuación.  
  
 Si no desea ofrecer la funcionalidad de aplicar al usuario, no es necesario quitar el botón Aplicar. Puede dejarla deshabilitada, como es habitual entre las aplicaciones que utilizan la compatibilidad de hoja de propiedades estándar disponible en versiones futuras de Windows.  
  
 Para informar de una página que se ha modificado y habilitar el botón Aplicar, llame a `CPropertyPage::SetModified( TRUE )`. Si cualquiera de los informes de páginas que se está modificando, el botón Aplicar permanecerá habilitado, independientemente de si se ha modificado la página activa actualmente.  
  
 Debe llamar a [CPropertyPage:: SetModified](../mfc/reference/cpropertypage-class.md#setmodified) cada vez que el usuario cambie cualquier configuración en la página. Una manera de detectar cuándo un usuario cambia un valor en la página consiste en implementar controladores de notificación de cambio para cada uno de los controles en la página de propiedades, como **EN_CHANGE** o **BN_CLICKED**.  
  
 Para implementar el efecto del botón Aplicar, la hoja de propiedades debe indicar su propietario o algún otro objeto externo en la aplicación, para aplicar la configuración actual en las páginas de propiedades. Al mismo tiempo, debe deshabilitar el botón Aplicar a la hoja de propiedades mediante una llamada a `CPropertyPage::SetModified( FALSE )` para todas las páginas que aplica sus modificaciones en el objeto externo.  
  
 Para obtener un ejemplo de este proceso, vea el ejemplo General de MFC [PROPDLG](../visual-cpp-samples.md).  
  
## <a name="see-also"></a>Vea también  
 [Hojas de propiedades](../mfc/property-sheets-mfc.md)

