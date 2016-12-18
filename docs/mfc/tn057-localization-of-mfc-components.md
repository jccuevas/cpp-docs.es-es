---
title: "TN057: Localizaci&#243;n de componentes de MFC | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.components"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "componentes [MFC], adaptar"
  - "DLL [C++], localizar en MFC"
  - "localización [C++], componentes de MFC"
  - "localización [C++], MFC (recursos)"
  - "localización [C++], recursos"
  - "DLL de MFC [C++], adaptar"
  - "recursos [MFC], adaptación"
  - "TN057"
ms.assetid: 5376d329-bd45-41bd-97f5-3d895a9a0af5
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN057: Localizaci&#243;n de componentes de MFC
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea.  Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos.  Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.  
  
 Esta nota describe algunos de los diseños y procedimientos que puede utilizar para localizar el componente, si dicho una aplicación o un control OLE o DLL que utiliza MFC.  
  
## Información general  
 Existe dos problemas para resolver cuando encuentra un componente que utiliza MFC.  Primero, debe localizar los recursos propios — cadenas, cuadros de diálogo, y otros recursos específicos del componente.  La mayoría de los componentes compilados mediante MFC también incluyen y utilizan varios recursos definidos por MFC.  Debe proporcionar recursos localizados de MFC también.  Afortunadamente, varios lenguajes proporciona ya por MFC.  
  
 Además, el componente debe estar preparado para ejecutarse en el entorno de destino \(entorno europeo o DBCS\- habilitado\).  En general, esto depende de la aplicación que trata los caracteres con el alto bit establecido correctamente y que administra las cadenas con caracteres de doble byte.  MFC está habilitada, de forma predeterminada, para ambos entornos, de modo que es posible tener un único binario mundial que se usa en todas las plataformas con solo distintos recursos enchufados en tiempo de instalación.  
  
## Adaptar recursos de componente  
 Adaptar la aplicación o DLL debe implicar simplemente reemplazando los recursos con recursos que coinciden con el idioma de destino.  Para los recursos propios, esto es relativamente simple: edite los recursos en el editor de recursos y compile la aplicación.  Si el código se escribe correctamente no habrá cadenas o texto que desea buscar codificadas de forma rígida en el código fuente de C\+\+ \(toda la localización puede ser hace simplemente modificar recursos.  De hecho, puede implementar el componente tales que todo proporcionar una versión localizada incluso no implica una compilación de código original.  Esto es más complejo, pero está bien digno de y es el mecanismo decidido MFC.  También es posible localizar una aplicación cargar el archivo EXE o DLL en el editor de recursos y editar los recursos directamente.  Aunque es posible, requiere el reapplication de esos cambios cada vez que compila una nueva versión de la aplicación.  
  
 Una manera de evitar que es buscar todos los recursos en un archivo DLL independiente, a veces denominado DLL satélite.  Esta DLL se carga dinámicamente en tiempo de ejecución y los recursos se cargan de ese archivo DLL en lugar del módulo principal con todo el código.  MFC admite directamente este enfoque.  Considere una aplicación denominada MYAPP.EXE; podría tener todos los recursos ubicados en una DLL denominada MYRES.DLL.  En `InitInstance` de aplicación realizar lo siguiente a la carga que DLL y causa MFC de cargar recursos desde esa ubicación:  
  
```  
CMyApp::InitInstance()  
{  
   // one of the first things in the init code  
   HINSTANCE hInst = LoadLibrary("myres.dll");  
   if (hInst != NULL)  
      AfxSetResourceHandle(hInst);  
  
   // other initialization code would follow  
   .  
   .  
   .  
}  
```  
  
 Desde entonces, MFC cargará recursos de ese archivo DLL en lugar de myapp.exe.  Todos los recursos, sin embargo, deben estar presentes en ese archivo DLL; MFC no buscará en la instancia de application en busca de un recurso determinado.  Esta técnica se aplica igualmente bien a archivos DLL y para los controles OLE regulares.  El programa de instalación copiaría la versión adecuada de MYRES.DLL dependiendo de que la configuración regional de recursos el usuario desea.  
  
 Es relativamente fácil crear un recurso sólo DLL.  Crea un proyecto de archivo DLL, agrega el archivo .RC a, y agrega los recursos necesarios.  Si tiene un proyecto existente que no utilice esta técnica, puede copiar recursos de ese proyecto.  Después de agregar el archivo de recursos al proyecto, está casi preparado para compilar el proyecto.  Lo único que debe hacer se establece las opciones del vinculador incluir **\/NOENTRY**.  Esto indica al vinculador que DLL no tiene ningún punto de entrada \(como no tiene ningún código, no tiene ningún punto de entrada.  
  
> [!NOTE]
>  El editor de recursos de Visual C\+\+ 4,0 y posterior admite varios idiomas por el archivo .RC.  Esto puede resultar muy fácil administrar la localización en un solo proyecto.  Las directivas de preprocesador controlan los recursos para cada lenguaje generadas por el editor de recursos.  
  
## Utilizando los recursos de Proporcionada MFC Traducidos  
 Cualquier aplicación MFC que se compile reutilizaciones dos cosas de MFC: código y recursos.  Es decir, MFC tiene diferentes mensajes de error, cuadros de diálogo integrados, y otros recursos que utilizan las clases MFC.  Para buscar completamente la aplicación, necesita buscar no solo los recursos de la aplicación, sino también a los recursos que proceden directamente de MFC.  MFC proporciona varios archivos de recursos de idioma automáticamente, de modo que si el lenguaje que esté destinado es uno de los lenguajes MFC admite ya, sólo deberá asegurarse de utilizar esos recursos localizados.  
  
 A partir de esta escritura, MFC admite chino, alemán, español, francés, español, japonés, y el coreano.  Los archivos que contienen estas versiones localizadas están en los directorios de MFC\\INCLUDE\\L.\* \(“l” representa localizado\).  Los archivos alemán están en MFC\\INCLUDE\\L.DEU, por ejemplo.  Para hacer que la aplicación para utilizar estos archivos RC en lugar de los archivos de MFC\\INCLUDE, agregue `/IC:\PROGRAM FILES\MICROSOFT VISUAL STUDIO .NET 2003\VC7\MFC\INCLUDE\L.DEU` a la línea de comandos RC \(esto es simplemente un ejemplo; necesitaría sustituir la configuración regional de la opción así como el directorio en el que instaló Visual C\+\+\).  
  
 Las instrucciones anteriores funcionarán si los vínculos de aplicación estáticamente a MFC.  La mayoría de las aplicaciones se vinculan dinámicamente \(porque es el valor predeterminado de AppWizard\).  En este escenario, no sólo el código se vincula dinámicamente – por lo que son los recursos.  Como resultado, puede buscar los recursos de la aplicación, pero los recursos de implementación de MFC todavía se cargarán MF C7 x.DLL \(o una versión posterior\) o MF C7 xLOC.DLL si existe.  Puede aproximarse a esto de dos distintos ángulos.  
  
 El enfoque más complejo es enviar uno MF localizada C7 xLOC.DLLs \(como xDEU MF C7, para el alemán, MF C7 xESP.DLL para español, etc.\)., o una versión posterior, e instala MF C7 adecuada xLOC.DLL en el directorio del sistema al instalar la aplicación.  Esto puede ser muy complejo para el programador y no se recomienda el usuario final y como tal.  Vea [Nota técnica 56](../mfc/tn056-installation-of-localized-mfc-components.md) para obtener más información sobre esta técnica y las advertencias.  
  
 El enfoque más sencillo y más seguro es incluir recursos localizados de MFC en la aplicación o el archivo DLL \(o el archivo DLL si usa uno\).  Esto evita problemas de instalar MF C7 xLOC.DLL correctamente.  Para ello, sigue las mismas instrucciones para el caso estático anterior \(estableciendo la línea de comandos RC correctamente el punto recursos adaptados\), excepto que debe quitar también `/D_AFXDLL` define que se agregó por AppWizard.  Cuando se define `/D_AFXDLL` , los AFXRES.H \(y los demás archivos de MFC RC\) no definen realmente a los recursos \(porque se extraerán de archivos DLL de MFC en su lugar\).  
  
## Vea también  
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)