---
title: 'Tutorial: Crear una aplicación UWP mediante WRL y Media Foundation | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: 0336c550-fbeb-4dc4-aa9b-660f9fc45382
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1c9e3f678a65b3dacfc5bba012656118b6fe2fa1
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33891690"
---
# <a name="walkthrough-creating-a-uwp-app-using-wrl-and-media-foundation"></a>Tutorial: Crear una aplicación UWP mediante WRL y Media Foundation
Obtenga información acerca de cómo usar la biblioteca de plantillas de C++ (WRL) de Windows en tiempo de ejecución para crear una aplicación de plataforma Universal de Windows (UWP) que usa [Microsoft Media Foundation](http://msdn.microsoft.com/library/windows/apps/ms694197).  
  
 Este ejemplo crea una transformación personalizada de Media Foundation que aplica un efecto de escala de grises a las imágenes capturadas con una cámara web. La aplicación utiliza C++ para definir la transformación personalizada y C# para usar el componente para transformar las imágenes capturadas.  
  
> [!NOTE]
>  En lugar de C#, también puede usar JavaScript, Visual Basic o C++ para utilizar el componente de transformación personalizado.  
  

 En la mayoría de los casos, puede utilizar C++ / CX para crear en tiempo de ejecución de Windows). Sin embargo, a veces deberá usar la WRL. Por ejemplo, cuando se crea una extensión de medios para Microsoft Media Foundation, debe crear un componente que implementa las interfaces COM y en tiempo de ejecución de Windows. Dado que C++ / CX solo puede crear objetos en tiempo de ejecución de Windows, para crear una extensión de medios debe usar la WRL porque permite la implementación de interfaces COM y en tiempo de ejecución de Windows.  

  
> [!NOTE]
>  Aunque este ejemplo de código es largo, muestra el mínimo necesario para crear una transformación útil de Media Foundation. Puede utilizarlo como punto de partida para su propia transformación personalizada. En este ejemplo se ha adaptado de la [ejemplo de extensiones de medios](http://code.msdn.microsoft.com/windowsapps/Media-extensions-sample-7b466096), que emplea extensiones de medios para aplicar efectos a vídeo, decodificar vídeo y crear controladores de esquema que generen secuencias multimedia.  
  
## <a name="prerequisites"></a>Requisitos previos  
  
-   Experiencia con el [en tiempo de ejecución de Windows](http://msdn.microsoft.com/library/windows/apps/br211377.aspx).  
  
-   Experiencia con COM.  
  
-   Cámara web.  
  
## <a name="key-points"></a>Puntos clave  
  
-   Para crear un componente personalizado de Media Foundation, utilice un archivo de definición de lenguaje de definición de interfaz de Microsoft (MIDL) para definir una interfaz, implemente esa interfaz y, a continuación, haga que se pueda activar desde otros componentes.  
  
-   El `namespace` y `runtimeclass` atributos y el `NTDDI_WIN8` [versión](http://msdn.microsoft.com/en-us/66ac5cf3-2230-44fd-aaf6-8013e4a4ae81) valor de atributo son partes importantes de la definición de MIDL para un componente de Media Foundation que usa WRL.  
  
-   [Microsoft::WRL::RuntimeClass](../windows/runtimeclass-class.md) es la clase base para el componente personalizado de Media Foundation. El [Microsoft::WRL::RuntimeClassType::WinRtClassicComMix](../windows/runtimeclasstype-enumeration.md) valor de enumeración, que se proporciona como un argumento de plantilla, marca la clase para su uso como una clase en tiempo de ejecución de Windows y como una clase en tiempo de ejecución de COM clásica.  
  
-   El [InspectableClass](../windows/inspectableclass-macro.md) macro implementa la funcionalidad básica de COM como recuento de referencias y el `QueryInterface` método y establece el tiempo de ejecución, nombre de clase y nivel de confianza.  
  
-   Usar el Microsoft:: wrl::[Module (clase)](https://www.microsoftonedoc.com/#/organizations/e6f6a65cf14f462597b64ac058dbe1d0/projects/3fedad16-eaf1-41a6-8f96-0c1949c68f32/containers/a3daf831-1c5f-4bbe-964d-503870caf874/tocpaths/b4acf5de-2f4c-4c8b-b5ff-9140d023ecbe/locales/en-US) para implementar funciones de punto de entrada de archivo DLL como [DllGetActivationFactory](http://msdn.microsoft.com/library/br205771.aspx), [DllCanUnloadNow](http://msdn.microsoft.com/library/windows/desktop/ms690368\(v=vs.85\).aspx), y [ DllGetClassObject](http://msdn.microsoft.com/library/windows/desktop/ms680760\(v=vs.85\).aspx).  
  
-   Vincule la DLL del componente a runtimeobject.lib. Especificar [/WINMD](../cppcx/compiler-and-linker-options-c-cx.md) en la línea del vinculador para generar los metadatos de Windows.  
  
-   Utilizar referencias de proyecto para que obtenga acceso a las aplicaciones UWP componentes WRL.  
  
### <a name="to-use-the-wrl-to-create-the-media-foundation-grayscale-transform-component"></a>Para usar la WRL para crear la escala de grises de Media Foundation transformar el componente  
  
1.  En Visual Studio, cree un **solución en blanco** proyecto. Nombre del proyecto, por ejemplo, `MediaCapture`.  
  
2.  Agregar un **DLL (Windows Universal)** proyecto a la solución. Nombre del proyecto, por ejemplo, `GrayscaleTransform`.  
  
3.  Agregar un **archivo Midl (.idl)** archivo al proyecto. Nombre del archivo, por ejemplo, `GrayscaleTransform.idl`.  
  
4.  Agregue este código a GrayscaleTransform.idl.  
  
     [!code-cpp[wrl-media-capture#1](../windows/codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_1.idl)]  
  
5.  Utilice el código siguiente para reemplazar el contenido de pch.h.  
  
     [!code-cpp[wrl-media-capture#2](../windows/codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_2.h)]  
  
6.  Agregue un nuevo archivo de encabezado al proyecto, asígnele el nombre `BufferLock.h`y, a continuación, agregue este código:  
  
     [!code-cpp[wrl-media-capture#3](../windows/codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_3.h)]  
  
7.  GrayscaleTransform.h no se utiliza en este ejemplo. Puede quitarlo del proyecto si lo desea.  
  
8.  Utilice el código siguiente para reemplazar el contenido de GrayscaleTransform.cpp.  
  
     [!code-cpp[wrl-media-capture#4](../windows/codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_4.cpp)]  
  
9. Agregue un nuevo archivo de definición de módulo al proyecto, asígnele el nombre `GrayscaleTransform.def`y, a continuación, agregue este código:  
  
   ```
   EXPORTS
       DllCanUnloadNow                     PRIVATE
       DllGetActivationFactory             PRIVATE
       DllGetClassObject                   PRIVATE
   ```   
  
10. Utilice el código siguiente para reemplazar el contenido de dllmain.cpp.  
  
     [!code-cpp[wrl-media-capture#6](../windows/codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_6.cpp)]  
  
11. En el proyecto **páginas de propiedades** diálogo cuadro, configure lo siguiente **vinculador** propiedades.  
  
    1.  En **entrada**, para la **archivo de definición de módulo**, especifique `GrayScaleTransform.def`.  
  
    2.  También en **entrada**, agregar `runtimeobject.lib`, `mfuuid.lib`, y `mfplatf.lib` a la **dependencias adicionales** propiedad.  
  
    3.  En **metadatos de Windows**, establezca **generar metadatos de Windows** a **Sí (/ WINMD)**.  
  
### <a name="to-use-the-wrl-the-custom-media-foundation-component-from-a-c-app"></a>Para usar la WRL el componente personalizado de Media Foundation desde una aplicación de C#  
  
1.  Agregue un nuevo **C# aplicación vacía (XAML)** proyecto a la `MediaCapture` solución. Nombre del proyecto, por ejemplo, `MediaCapture`.  
  
2.  En el **MediaCapture** del proyecto, agregue una referencia a la `GrayscaleTransform` proyecto. Para obtener información sobre cómo hacerlo, consulte [Cómo: agregar o quitar referencias mediante el Administrador de referencias](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager).  
  
3.  En Package.appxmanifest, en la **capacidades** ficha, seleccione **micrófono** y **cámara Web**. Ambas capacidades son necesarias para capturar fotografías con la cámara web.  
  
4.  En MainPage.xaml, agregue este código a la raíz [cuadrícula](http://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.grid.aspx) elemento:  
  
     [!code-xml[wrl-media-capture#7](../windows/codesnippet/Xaml/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_7.xaml)]  
  
5.  Utilice el código siguiente para reemplazar el contenido de MainPage.xaml.cs.  
  
     [!code-cs[wrl-media-capture#8](../windows/codesnippet/CSharp/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_8.cs)]  
  
 En la siguiente ilustración se muestra la aplicación MediaCapture.  
  
 ![Aplicación MediaCapture que captura una foto](../windows/media/wrl_media_capture.png "WRL_Media_Capture")  
  
## <a name="next-steps"></a>Pasos siguientes  
 En el ejemplo se muestra cómo capturar fotografías con la cámara web predeterminada de una en una. El [ejemplo de extensiones de medios](http://code.msdn.microsoft.com/windowsapps/Media-extensions-sample-7b466096) hace más. Muestra cómo enumerar los dispositivos de cámara web y trabajar con controladores de esquema locales, además de mostrar los efectos de medios adicionales que funcionan en fotos individuales y secuencias de vídeo.  
  
## <a name="see-also"></a>Vea también  
 [Biblioteca de plantillas C++ de Windows en tiempo de ejecución (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)   
 [Microsoft Media Foundation](http://msdn.microsoft.com/library/windows/apps/ms694197)   
 [Ejemplo de extensiones de medios](http://code.msdn.microsoft.com/windowsapps/Media-extensions-sample-7b466096)