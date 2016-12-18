---
title: "Implementing Property Pages | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IPropertyPage class"
  - "IPropertyPage2 class"
  - "páginas de propiedades, implementar"
ms.assetid: 62f29440-33a7-40eb-a1ef-3634c95f640c
caps.latest.revision: 11
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Implementing Property Pages
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las páginas de propiedades son objetos COM que implementan `IPropertyPage` o la interfaz de **IPropertyPage2** .  ATL proporciona compatibilidad para implementar páginas de propiedades con [Asistente para páginas de propiedades ATL](../atl/reference/atl-property-page-wizard.md) en [agregue el cuadro de diálogo de la clase](../ide/add-class-dialog-box.md).  
  
 Para crear una página de propiedades mediante ATL:  
  
-   Cree o abra un proyecto de servidor de \(DLL\) de biblioteca de vínculos dinámicos de ATL.  
  
-   Abra [agregue el cuadro de diálogo de la clase](../ide/add-class-dialog-box.md) y seleccione **Página de propiedades ATL**.  
  
-   Asegúrese de que la página de propiedades sea apartamento de subproceso \(dado que tiene una interfaz de usuario\).  
  
-   Establezca el título, descripción \(Documento String\), y el archivo de ayuda que se asociarán a la página.  
  
-   Agregue controles al recurso representado del diálogo para que actúe como la interfaz de usuario de la página de propiedades.  
  
-   Responder a los cambios en la interfaz de usuario de la página para realizar la validación, actualice el sitio de la página, o actualizar los objetos asociados a la página.  En particular, llamada [IPropertyPageImpl::SetDirty](../Topic/IPropertyPageImpl::SetDirty.md) cuando el usuario realiza cambios en la página de propiedades.  
  
-   Reemplace opcionalmente los métodos de `IPropertyPageImpl` mediante las instrucciones siguientes.  
  
    |Método de IPropertyPageImpl|Reemplace si desea…|Notas|  
    |---------------------------------|-------------------------|-----------|  
    |[SetObjects](../Topic/IPropertyPageImpl::SetObjects.md)|Realice las comprobaciones básicas de la cordura en el número de objetos que se pasan a la página y las interfaces que admiten.|Ejecute su propio código antes de llamar a la implementación de la clase base.  Si los objetos que especifica no cumplen sus expectativas, se debe superar la llamada lo más rápidamente posible.|  
    |[Active](../Topic/IPropertyPageImpl::Activate.md)|Inicializa la interfaz de usuario de la página \(por ejemplo, establecer los controles de cuadro de diálogo con valores de propiedad actuales de objetos, cree los controles chart, o realizar otras inicializaciones\).|Llame a la implementación de la clase base antes de que el código de modo que la clase base tiene una oportunidad de crear la ventana cuadro de diálogo y todos los controles antes de intentar actualizarlos.|  
    |[Aplicar](../Topic/IPropertyPageImpl::Apply.md)|Valide los valores de propiedades y actualizar los objetos.|No hay necesidad de llamar a la implementación de la clase base como no hace nada aparte de traza llamada.|  
    |[Desactivar](../Topic/IPropertyPageImpl::Deactivate.md)|Elimine los elementos ventana\- relacionados.|La implementación de la clase base destruye el cuadro de diálogo que representa la página de propiedades.  Si necesita limpiar antes de que se destruya el cuadro de diálogo, debe agregar el código antes de llamar a la clase base.|  
  
 Para una aplicación de la página de propiedades de ejemplo, vea [ejemplo: implementar una página de propiedades](../atl/example-implementing-a-property-page.md).  
  
> [!NOTE]
>  Si desea hospedar controles ActiveX en la página de propiedades, deberá cambiar la derivación de la clase asistente\- generada.  Reemplace **CDialogImpl\<CYourClass\>** con **CAxDialogImpl\<CYourClass\>** en la lista de clases base.  
  
## Vea también  
 [Páginas de propiedades](../atl/atl-com-property-pages.md)   
 [Ejemplo ATLPages](../top/visual-cpp-samples.md)