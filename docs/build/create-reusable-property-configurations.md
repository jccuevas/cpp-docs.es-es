---
title: 'Uso compartido o reutilización de la configuración del proyecto de Visual Studio: C++'
ms.date: 07/17/2019
helpviewer_keywords:
- project properties [C++], reusable
ms.openlocfilehash: bcf54be0531c7150c1506eb6f5dda2b5bc95161f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328698"
---
# <a name="share-or-reuse-visual-studio-project-settings"></a>Uso compartido o reutilización de la configuración del proyecto de Visual Studio

Para crear un grupo personalizado de opciones de configuración que se puedan compartir con otros usuarios o reutilizar en varios proyectos, use el **Administrador de propiedades** para crear una *hoja de propiedades* (archivo .props) para almacenar la configuración de cada tipo de proyecto que quiera poder reutilizar o compartir con otros usuarios. El uso de hojas de propiedades es mucho menos propenso a errores que otras formas de crear una configuración "global".

> [!IMPORTANT]
> **Los archivos .user y las razones por las que son problemáticos**
>
> En las versiones anteriores de Visual Studio se usaban hojas de propiedades globales que tenían una extensión de nombre de archivo .user y se encontraban en la carpeta \<PerfilDeUsuario>\AppData\Local\Microsoft\MSBuild\v4.0\. Ya no recomendamos estos archivos porque establecen propiedades para configuración de proyecto por usuario y por equipo. Estos valores "globales" pueden interferir con las compilaciones, especialmente cuando tenga como destino varias plataformas en el equipo de compilación. Por ejemplo, si tiene un proyecto MFC y un proyecto de Windows Phone, las propiedades .user no serían válidas para uno de ellos. Las hojas de propiedades reutilizables son más flexibles y más eficaces.
>
> Aunque los archivos .user todavía se instalan con Visual Studio y participan en la herencia de propiedades, están vacíos de forma predeterminada. El procedimiento recomendado es eliminar la referencia a ellos en el **Administrador de propiedades** para asegurarse de que los proyectos funcionan independientemente de cualquier configuración por usuario y por equipo. Esto es importante para asegurar un comportamiento correcto en un entorno SCC (control de código fuente).

Para mostrar el **Administrador de propiedades**, en la barra de menús elija **Ver** > **Administrador de propiedades** o **Ver** > **Otras ventanas** > **Administrador de propiedades**, en función de la configuración.

Si tiene un conjunto de propiedades común que usa con frecuencia y que quiera aplicar a varios proyectos, puede usar el **Administrador de propiedades** para capturarlas en un archivo de *hoja de propiedades* reutilizable, que por convención tiene una extensión de nombre de archivo .props. Puede aplicar la hoja (u hojas) a nuevos proyectos para que no tenga que establecer sus propiedades desde cero.

![Menú contextual del Administrador de propiedades](media/sharingnew.png "SharingNew")

En cada nodo de configuración, podrá ver los nodos para cada hoja de propiedades que se aplica a esa configuración. El sistema agrega hojas de propiedades que establecen valores en función de las opciones que se elijan en el Asistente para aplicaciones al crear el proyecto. Haga clic con el botón derecho en cualquier nodo y seleccione Propiedades para ver las propiedades que se aplican a ese nodo. Todas las hojas de propiedades se importan de manera automática en la hoja de propiedades "maestra" del proyecto (ms.cpp.props) y se evalúan en el orden en que aparecen en el Administrador de propiedades. Se pueden mover para cambiar el orden de evaluación. Las hojas de propiedades que se evalúan después invalidarán los valores de las hojas evaluadas anteriormente. Vea [Herencia de propiedades del proyecto](project-property-inheritance.md) para obtener más información sobre el orden de evaluación en el archivo .vcxproj, los archivos .props y .targets, las variables de entorno y la línea de comandos.

Si hace clic en **Agregar nueva hoja de propiedades de proyecto** y selecciona, por ejemplo, la hoja de propiedades MyProps.props, aparecerá un cuadro de diálogo de página de propiedades. Observe que se aplica a la hoja de propiedades MyProps; los cambios que realice se escriben en la hoja, no en el archivo de proyecto (.vcxproj).

Las propiedades en una hoja de propiedades se invalidan si la misma propiedad se establece directamente en el archivo .vcxproj.

Puede importar una hoja de propiedades con tanta frecuencia como sea necesaria. Varios proyectos de una solución pueden heredar valores de la misma hoja de propiedades y un proyecto puede tener varias hojas. Una hoja de propiedades en sí misma puede heredar la configuración de otra hoja de propiedades.

También puede crear una hoja de propiedades para varias configuraciones. Para ello, cree una hoja de propiedades para cada configuración, abra el menú contextual para una de ellas, seleccione **Agregar hoja de propiedades existente** y, después, agregue las demás hojas. Sin embargo, si utiliza una hoja de propiedades comunes, tenga en cuenta que, cuando se establece una propiedad, obtiene el conjunto de todas las configuraciones a las que se aplica la hoja y el IDE no muestra los proyectos u hojas de propiedades que heredan valores de una hoja de propiedades determinada.

En soluciones grandes que tendrán muchos proyectos, puede ser útil crear una hoja de propiedades en el nivel de solución. Al agregar un proyecto a la solución, use el **Administrador de propiedades** para agregar esa hoja de propiedades al proyecto. Si se solicita en el nivel de proyecto, puede agregar una nueva hoja de propiedades para establecer valores específicos del proyecto.

> [!IMPORTANT]
> Los archivos .props no participan de forma predeterminada en el control de código fuente porque no se crean como elemento del proyecto. Puede agregar manualmente el archivo como elemento de la solución si desea incluirlo en el control de código fuente.

#### <a name="to-create-a-property-sheet"></a>Para crear una hoja de propiedades

1. En la barra de menús, elija **Ver** > **Administrador de propiedades** o **Ver** > **Otras ventanas** > **Administrador de propiedades**. Se abrirá el **Administrador de propiedades**.

2. Para definir el ámbito de la hoja de propiedades, seleccione el elemento al que se aplica. Puede ser una configuración concreta u otra hoja de propiedades. Abra el menú contextual para este elemento y después seleccione **Agregar nueva hoja de propiedades de proyecto**. Especifique un nombre y una ubicación.

3. En el **Administrador de propiedades**, abra la hoja de propiedades nueva y después establezca las propiedades que quiera incluir.
