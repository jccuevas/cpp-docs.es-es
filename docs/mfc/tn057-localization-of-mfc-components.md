---
title: 'TN057: Localización de componentes de MFC | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.mfc.components
dev_langs:
- C++
helpviewer_keywords:
- components [MFC], localizing
- TN057
- resources [MFC], localization
- localization [MFC], MFC resources
- localization [MFC], MFC components
- MFC DLLs [MFC], localizing
- DLLs [MFC], localizing MFC
- localization [MFC], resources
ms.assetid: 5376d329-bd45-41bd-97f5-3d895a9a0af5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 935f85f55db8ed0d01bce309aa598100002c0f4d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33384519"
---
# <a name="tn057-localization-of-mfc-components"></a>TN057: Localización de componentes de MFC
> [!NOTE]
>  La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea. Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos. Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.  
  
 Esta nota describe algunos de los diseños y procedimientos que puede usar para localizar el componente, si se controla una aplicación o una OLE o un archivo DLL que utiliza MFC.  
  
## <a name="overview"></a>Información general  
 Realmente hay dos problemas para resolver cuando localiza un componente que utiliza MFC. En primer lugar, debe localizar sus propios recursos: cadenas, los cuadros de diálogo y otros recursos que son específicos de su componente. Mayoría de los componentes creada con MFC también incluye y utiliza un número de recursos que se definen mediante MFC. Debe proporcionar también los recursos MFC localizados. Afortunadamente, MFC propio ya proporciona varios idiomas.  
  
 Además, el componente debe estar preparado para ejecutarse en su entorno de destino (entorno Europeo o habilitados para DBCS). En general, esto depende de la aplicación, tratar correctamente los caracteres con el conjunto de bits y control de cadenas con caracteres de doble byte. MFC está habilitada de forma predeterminada, tanto de estos entornos, para que sea posible tener un solo binario en todo el mundo que se usa en todas las plataformas con diferentes recursos enchufados durante la instalación.  
  
## <a name="localizing-your-components-resources"></a>Adaptar recursos de su componente  
 Localizar la aplicación o el archivo DLL debe implican simplemente reemplazar los recursos con los recursos que coinciden con el idioma de destino. Para obtener sus propios recursos, esto es relativamente sencilla: modificar los recursos en el editor de recursos y compile la aplicación. Si se escribe el código correctamente no habrá ningún cadenas o el texto que desea localizar codificado de forma rígida en el código fuente de C++ - toda la localización puede realizarse modificando simplemente recursos. De hecho, puede implementar el componente de modo que todos los que proporciona una versión localizada implican incluso una compilación del código original. Esto es más complejo, pero también merece la pena y es el mecanismo elegido para MFC. También es posible localizar una aplicación carga el archivo EXE o DLL en el editor de recursos y modificar directamente los recursos. Aunque es posible, requiere volver a aplicar esos cambios cada vez que se genere una nueva versión de la aplicación.  
  
 Una manera de evitar consiste en ubicar todos los recursos en una archivo DLL independiente, a veces denominada un archivo DLL satélite. Este archivo DLL, a continuación, se carga dinámicamente en tiempo de ejecución y los recursos se cargan desde esa DLL en lugar de desde el módulo principal con todo el código. MFC admite directamente este enfoque. Considere la posibilidad de una aplicación denominada MYAPP. EXE; Esto podría tener todos sus recursos ubicados en un archivo DLL denominado MYRES. DLL. En la aplicación `InitInstance` realizaría lo siguiente para cargar ese archivo DLL y hacer que MFC cargar recursos desde esa ubicación:  
  
```  
CMyApp::InitInstance()  
{ *// one of the first things in the init code  
    HINSTANCE hInst = LoadLibrary("myres.dll");

    if (hInst != NULL)  
    AfxSetResourceHandle(hInst);

 *// other initialization code would follow  
 .  
 .  
 .  
}  
```  
  
 Desde ese momento, MFC cargará los recursos de ese archivo DLL en lugar de desde myapp.exe. Todos los recursos, sin embargo, deben estar presentes en ese archivo DLL; MFC no buscará en la instancia de la aplicación en busca de un recurso determinado. Esta técnica aplica igualmente bien a regular archivos DLL de MFC como controles OLE. El programa de instalación copie la versión adecuada de MYRES. Dependiendo de qué configuración regional de recursos DLL en la que desea que el usuario.  
  
 Es relativamente fácil crear un recurso solo DLL. Crear un proyecto DLL, agregue su. RC de archivos en él y agregue los recursos necesarios. Si tiene un proyecto existente que no use esta técnica, puede copiar los recursos de ese proyecto. Después de agregar el archivo de recursos al proyecto, está casi listo para compilar el proyecto. Lo único que debe hacer es establecer las opciones para incluir el vinculador **/NOENTRY**. Esto indica al vinculador que el archivo DLL no tiene ningún punto de entrada - ya que no tiene ningún código, no tiene ningún punto de entrada.  
  
> [!NOTE]
>  El editor de recursos en Visual C++ 4.0 y versiones posteriores admite varios idiomas por. Archivo RC. Esto puede hacer muy fácil de administrar la localización en un solo proyecto. Los recursos para cada idioma se controlan mediante directivas de preprocesador generadas por el editor de recursos.  
  
## <a name="using-the-provided-mfc-localized-resources"></a>Mediante la MFC proporcionado recursos localizados  
 Cualquier aplicación MFC que compile vuelve a utilizar dos cosas de MFC: código y recursos. Es decir, MFC tiene varios mensajes de error, cuadros de diálogo integrados y otros recursos que son utilizadas por las clases MFC. Para localizar completamente la aplicación, debe localizar no solo a los recursos de la aplicación, sino también a los recursos que procedan directamente de MFC. MFC proporciona a una serie de idioma diferentes archivos de recursos automáticamente, por lo que si el idioma de destino es uno de los idiomas ya es compatible con la MFC, solo tiene que asegurarse de que usar esos recursos localizados.  
  
 Cuando se redactó este documento, MFC admite chino, alemán, español, francés, italiano, japonés y coreano. Los archivos que contienen estas versiones localizadas están en el MFC\INCLUDE\L.* ('L' representa para localizar) directorios. Los archivos de alemán están en MFC\INCLUDE\L.DEU, por ejemplo. Para hacer que la aplicación para usar estos RC (archivos) en lugar de los archivos ubicados en MFC\INCLUDE, agregue un `/IC:\PROGRAM FILES\MICROSOFT VISUAL STUDIO .NET 2003\VC7\MFC\INCLUDE\L.DEU` a la línea de comandos RC (Esto es simplemente un ejemplo; quizá necesite sustituir la configuración regional de elección, así como el directorio en el que instaló Visual C ++).  
  
 Las instrucciones anteriores funcionará si la aplicación se vincula estáticamente a MFC. Mayoría de las aplicaciones de vínculo dinámicamente (ya que es el valor predeterminado de AppWizard). En este escenario, no solo el código es dinámicamente vinculado - son por lo que los recursos. Como resultado, puede localizar los recursos en la aplicación, pero los recursos de implementación de MFC se cargará desde el MFC7x.DLL (o una versión posterior) o desde MFC7xLOC.DLL si existe. Se puede enfocar desde distintos dos ángulos.  
  
 El enfoque más complejo es directa entre el MFC7xLOC.DLLs localizado (por ejemplo, MFC7xDEU, alemán, MFC7xESP.DLL para español, etc.) o una versión posterior e instalar la MFC7xLOC.DLL adecuada en el directorio del sistema cuando el usuario instala la aplicación. Esto puede ser muy complejo para que el desarrollador y el usuario final y por lo tanto no se recomienda. Vea [56 de nota técnica](../mfc/tn056-installation-of-localized-mfc-components.md) para obtener más información sobre esta técnica y sus cláusulas.  
  
 El enfoque más sencillo y más seguro es incluir los recursos MFC localizados en la aplicación o DLL propio (o su DLL satélite si está usando uno). Esto evita los problemas de instalación MFC7xLOC.DLL correctamente. Para ello, siga las mismas instrucciones para el caso estático indicadas anteriormente (configuración de la línea de comandos RC correctamente para que apunte a los recursos localizados), salvo que también debe quitar la `/D_AFXDLL` define y que se ha agregado por el Asistente para aplicaciones. Cuando `/D_AFXDLL` está definido, AFXRES. H (y los demás archivos de MFC RC) no define los recursos (debido a se van a extraer de los archivos DLL de MFC en su lugar).  
  
## <a name="see-also"></a>Vea también  
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)

