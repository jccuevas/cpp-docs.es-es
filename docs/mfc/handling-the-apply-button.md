---
title: Controlar el botón Aplicar
ms.date: 11/04/2016
helpviewer_keywords:
- Apply button in property sheet
- property sheets, Apply button
ms.assetid: 7e977015-59b8-406f-b545-aad0bfd8d55b
ms.openlocfilehash: 30ee549a334a684deeb4a845f2fc49ee8bbe11db
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62240592"
---
# <a name="handling-the-apply-button"></a>Controlar el botón Aplicar

Hojas de propiedades tienen una funcionalidad que no lo hacen los cuadros de diálogo estándar: Permiten que el usuario aplicar los cambios que se hayan realizado antes de cerrar la hoja de propiedades. Esto se realiza mediante el botón Aplicar. En este artículo se describe los métodos que puede usar para implementar correctamente esta característica.

Cuadros de diálogo modales suelen aplican la configuración a un objeto externo cuando el usuario hace clic en Aceptar para cerrar el cuadro de diálogo. Lo mismo puede decirse de una hoja de propiedades: Cuando el usuario hace clic en Aceptar, aplicará la nueva configuración en la hoja de propiedades.

Sin embargo, desea permitir al usuario guardar la configuración sin tener que cerrar el cuadro de diálogo de la hoja de propiedades. Se trata de la función del botón Aplicar. El botón Aplicar aplica la configuración actual en todas las páginas de propiedades para el objeto externo, en lugar de aplicarse solo la configuración actual de la página activa actualmente.

De forma predeterminada, el botón Aplicar siempre está deshabilitado. Debe escribir código para habilitar el botón Aplicar en el momento adecuado, y debe escribir código para implementar el efecto de aplicar, tal como se explica más adelante.

Si no desea ofrecer la funcionalidad de aplicar al usuario, no es necesario quitar el botón Aplicar. Puede dejarlo deshabilitado, como es habitual entre las aplicaciones que usan el soporte técnico de hoja de propiedades estándar disponible en versiones futuras de Windows.

Para informar de una página que se ha modificado y habilitar el botón Aplicar, llame a `CPropertyPage::SetModified( TRUE )`. Si cualquiera de los que se está modificando el informe de páginas, el botón Aplicar permanecerá habilitado, independientemente de si se ha modificado la página activa actualmente.

Debe llamar a [CPropertyPage:: SetModified](../mfc/reference/cpropertypage-class.md#setmodified) cada vez que el usuario cambia cualquier configuración en la página. Una manera de detectar cuándo un usuario cambia un valor en la página consiste en implementar controladores de notificación de cambio para cada uno de los controles en la página de propiedades, como **EN_CHANGE** o **BN_CLICKED**.

Para implementar el efecto del botón Aplicar, la hoja de propiedades debe indicar su propietario, o algún otro objeto externo en la aplicación, para aplicar la configuración actual en las páginas de propiedades. Al mismo tiempo, debe deshabilitar el botón Aplicar a la hoja de propiedades mediante una llamada a `CPropertyPage::SetModified( FALSE )` para todas las páginas que aplica sus modificaciones en el objeto externo.

Para obtener un ejemplo de este proceso, vea el ejemplo General de MFC [PROPDLG](../overview/visual-cpp-samples.md).

## <a name="see-also"></a>Vea también

[Hojas de propiedades](../mfc/property-sheets-mfc.md)
