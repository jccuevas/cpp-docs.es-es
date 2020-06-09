---
title: Controlar el botón Aplicar
ms.date: 11/04/2016
helpviewer_keywords:
- Apply button in property sheet
- property sheets, Apply button
ms.assetid: 7e977015-59b8-406f-b545-aad0bfd8d55b
ms.openlocfilehash: cd1254a31491e713513f0db0d4cf87baddd9bb23
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618616"
---
# <a name="handling-the-apply-button"></a>Controlar el botón Aplicar

Las hojas de propiedades tienen una funcionalidad que los cuadros de diálogo estándar no: permiten al usuario aplicar los cambios realizados antes de cerrar la hoja de propiedades. Esto se hace mediante el botón aplicar. En este artículo se describen los métodos que puede usar para implementar esta característica correctamente.

Los cuadros de diálogo modales suelen aplicar la configuración a un objeto externo cuando el usuario hace clic en Aceptar para cerrar el cuadro de diálogo. Lo mismo se cumple para una hoja de propiedades: cuando el usuario hace clic en aceptar, se aplica la nueva configuración de la hoja de propiedades.

Sin embargo, puede que desee permitir que el usuario guarde la configuración sin tener que cerrar el cuadro de diálogo hoja de propiedades. Esta es la función del botón aplicar. El botón aplicar aplica la configuración actual de todas las páginas de propiedades al objeto externo, en lugar de aplicar solo la configuración actual de la página activa actualmente.

De forma predeterminada, el botón aplicar está siempre deshabilitado. Debe escribir código para habilitar el botón aplicar en las horas apropiadas y debe escribir código para implementar el efecto de aplicar, como se explica a continuación.

Si no desea ofrecer la funcionalidad de aplicación al usuario, no es necesario quitar el botón aplicar. Puede dejarlo deshabilitado, tal y como será común entre las aplicaciones que usan la compatibilidad con la hoja de propiedades estándar disponible en versiones futuras de Windows.

Para notificar una página como modificada y habilitar el botón aplicar, llame a `CPropertyPage::SetModified( TRUE )` . Si se está modificando alguna de las páginas del informe, el botón aplicar permanecerá habilitado, independientemente de si se ha modificado la página activa actualmente.

Debe llamar a [CPropertyPage:: SetModified](reference/cpropertypage-class.md#setmodified) cada vez que el usuario cambie cualquier configuración de la página. Una manera de detectar cuándo un usuario cambia una configuración en la página es implementar controladores de notificación de cambios para cada uno de los controles de la página de propiedades, como **EN_CHANGE** o **BN_CLICKED**.

Para implementar el efecto del botón aplicar, la hoja de propiedades debe indicar a su propietario, o algún otro objeto externo de la aplicación, que aplique la configuración actual en las páginas de propiedades. Al mismo tiempo, la hoja de propiedades debe deshabilitar el botón aplicar llamando a `CPropertyPage::SetModified( FALSE )` para todas las páginas que han aplicado sus modificaciones en el objeto externo.

Para obtener un ejemplo de este proceso, vea el ejemplo general de MFC [PROPDLG](../overview/visual-cpp-samples.md).

## <a name="see-also"></a>Consulte también

[Hojas de propiedades](property-sheets-mfc.md)
