---
title: Propiedades estándar | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- stock properties, about stock properties
- stock properties
ms.assetid: a89fc454-0b8e-447a-9033-4c8af46a24d9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 201e6f0591d446dc0e6b036cfd7ac6f3028eb812
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46430272"
---
# <a name="stock-properties"></a>Propiedades estándar

Si se va a agregar una propiedad a una interfaz dispinterface de MFC mediante el [Asistente para agregar propiedades](../ide/idl-attributes-add-property-wizard.md), se puede elegir una propiedad estándar de la lista **Nombre de la propiedad** en la página [Nombres](../ide/names-add-property-wizard.md) del asistente. Estas propiedades son las siguientes:

|Nombre de la propiedad|Descripción|
|-------------------|-----------------|
|**Apariencia**|Devuelve o establece un valor que determina la apariencia del control. La propiedad **Apariencia** del control puede incluir u omitir efectos de presentación tridimensionales. Se trata de una propiedad de ambiente de lectura y escritura.|
|`BackColor`|Devuelve o establece la propiedad `BackColor` de ambiente del control en un color de paleta (RGB) o un color del sistema predefinido. De forma predeterminada, su valor se corresponde al color de primer plano del contenedor del control. Se trata de una propiedad de ambiente de lectura y escritura.|
|`BorderStyle`|Devuelve o establece el estilo de borde para un control. Es una propiedad de lectura y escritura.|
|**Título**|Devuelve o establece la propiedad **Título** del control. El título es el título de la ventana. **Título** no tiene ningún tipo de implementación **Variable miembro**.|
|**Habilitado**|Devuelve o establece la propiedad **Habilitado** del control. Un control habilitado puede responder a eventos generados por el usuario.|
|**Fuente**|Devuelve o establece la fuente de ambiente del control. Es NULL si el control no tiene ninguna fuente.|
|`ForeColor`|Devuelve o establece la propiedad `ForeColor` de ambiente del control.|
|**hWnd**|Devuelve o establece la propiedad **hWnd** de ambiente del control. **hWnd** no tiene ningún tipo de implementación **Variable miembro**.|
|**ReadyState**|Devuelve o establece la propiedad **ReadyState** del control. Un control puede estar no inicializado, inicializado, cargando, interactivo o completo. Vea [READYSTATE](https://msdn.microsoft.com/library/aa768362.aspx) en el *SDK de Internet* para obtener más información.|
|**Texto**|Devuelve o establece el texto contenido en un control. **Texto** no tiene ningún tipo de implementación **Variable miembro**.|

## <a name="see-also"></a>Vea también

[Agregar una propiedad](../ide/adding-a-property-visual-cpp.md)<br>
[Atributos IDL, Asistente para agregar propiedades](../ide/idl-attributes-add-property-wizard.md)