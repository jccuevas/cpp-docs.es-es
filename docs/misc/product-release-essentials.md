---
title: "Conceptos b&#225;sicos de la versi&#243;n de producto | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "implementación, conceptos básicos"
  - "instalación [SDK de Visual Studio], conceptos básicos"
ms.assetid: 28370bc8-f3a7-4c5e-9b35-8331cda14ff4
caps.latest.revision: 12
caps.handback.revision: 12
manager: "douge"
---
# Conceptos b&#225;sicos de la versi&#243;n de producto
Una experiencia de instalación agradable y eficiente genera una impresión duradera en las mentes de los usuarios sobre el producto de integración de [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]. Una experiencia de instalación desagradable también genera una impresión duradera, por lo que la aplicación de los siguientes procedimientos recomendados en el desarrollo y la prueba de la instalación vale la inversión.  
  
## Desarrollar de paquetes de instalación de Windows Installer  
 Windows Installer es el servicio recomendado de instalación y configuración para Windows y los productos de integración de [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)].  
  
> [!NOTE]
>  La documentación de [!INCLUDE[vsipsdk](../mfc/includes/vsipsdk_md.md)] sobre la instalación de productos de integración de [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] se basa en conceptos de Windows Installer, pero no abarca Windows Installer en sí. Para obtener vínculos a las secciones relevantes de la documentación de Windows Installer, consulte la tabla siguiente.  
  
 En el contexto de la instalación, *componente* hace referencia a un componente de Windows Installer. Los componentes tienen recursos como archivos y entradas del Registro y se instalan y se quitan como una unidad.  
  
|Tarea|Para obtener más información, vea|  
|-----------|---------------------------------------|  
|Más información sobre Windows Installer.|[Windows Installer](http://msdn.microsoft.com/library/aa372866.aspx)|  
|Determinar los requisitos del sistema de su VSPackage.|-   [Detectar los requisitos del sistema](../Topic/Detecting%20System%20Requirements.md)|  
|Obtener información sobre cómo registrar un VSPackage en un paquete de instalación.|-   [Registro de VSPackage](../Topic/VSPackage%20Registration.md)<br />-   [Comandos que se deben ejecutar después de la instalación](../Topic/Commands%20That%20Must%20Be%20Run%20After%20Installation.md)|  
|Ver un paquete de instalación de ejemplo.|-   Ejemplo de configuración de la integración de IronPython|  
  
## Admitir productos en paralelo  
 El término En paralelo \(a veces abreviado como *SxS* por su término en inglés "side\-by\-side"\) hace referencia a la capacidad de tener instaladas varias versiones del mismo producto, e incluso en ejecución, al mismo tiempo. Para los productos de integración de [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)], también hace referencia al hecho de que [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] admite la ejecución en paralelo.  
  
|Tarea|Para obtener más información, vea|  
|-----------|---------------------------------------|  
|Obtener información sobre la compatibilidad con varias versiones de [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] en el producto de integración de [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)].|-   [Elegir entre VSPackages compartido y su versión](../Topic/Choosing%20Between%20Shared%20and%20Versioned%20VSPackages.md)<br />-   [Administración de componentes](../Topic/Component%20Management.md)|  
|Obtener información sobre la compatibilidad con varias versiones del producto de integración de [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)].|-   [Elegir entre VSPackages compartido y su versión](../Topic/Choosing%20Between%20Shared%20and%20Versioned%20VSPackages.md)<br />-   [Registrar extensiones de nombre de archivo para las implementaciones en paralelo](../Topic/Registering%20File%20Name%20Extensions%20for%20Side-By-Side%20Deployments.md)<br />-   [Detectar los requisitos del sistema](../Topic/Detecting%20System%20Requirements.md)<br />-   [Comandos que se deben ejecutar después de la instalación](../Topic/Commands%20That%20Must%20Be%20Run%20After%20Installation.md)|  
  
## Probar el producto de integración de Visual Studio  
 El conjunto de pruebas de integración \(VSIT\) de [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] consiste en una serie de pruebas destinadas a comprobar que un paquete VSPackage se integra correctamente en [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]. VSIT no prueba las funciones de un paquete VSPackage, pero ayuda a garantizar que un paquete VSPackage no afecta negativamente a otras funciones de [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]. Para obtener más información, consulte [Visual Studio Integration Tests](http://msdn.microsoft.com/es-es/8d741735-7d93-46c2-ab93-01da7a0e016d).