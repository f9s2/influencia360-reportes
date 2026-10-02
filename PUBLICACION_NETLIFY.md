# Publicación de Influencia360 en Netlify

## Estado y contenido

Esta carpeta es una copia independiente del repositorio público `rubendcl/Influencers` (commit de origen `a1b6d2c`). Los HTML de `docs/` coinciden con ese origen. La publicación en internet sigue pendiente: no hay una cuenta de Netlify conectada en esta sesión.

El sitio está preparado para publicar como contenido estático, sin servidor de R ni compilación en Netlify. `netlify.toml` indica `docs` como directorio de publicación. La portada `index.html` enlaza a los dos reportes requeridos:

- `/dashboard_datos.html`: exploración interactiva de los perfiles, publicaciones, relaciones e interacciones ficticias.
- `/dashboard_resultados.html`: resultados bayesianos, ranking de influenciadores y escenarios de inferencia.

También se publica `/index.html`, el informe metodológico y ejecutivo. Los HTML tienen los recursos incorporados y pesan aproximadamente 8,7 MB, 10,1 MB y 10,1 MB, respectivamente. Al abrir cada URL, Netlify entrega el archivo desde su red de distribución. Para actualizar los datos, se debe volver a generar el contenido con `Rscript run_all.R` en un entorno que tenga R y los paquetes requeridos, y desplegar nuevamente `docs/`.

## Despliegue previsto

En Netlify, importar el repositorio `rubendcl/Influencers` de GitHub o una copia propia de esta carpeta y usar la raíz como directorio base. Directorio de publicación: `docs`; comando de compilación: vacío. Otra opción es desplegar manualmente `docs/` con Netlify CLI. Netlify Drop permite arrastrar esa carpeta, aunque la documentación advierte que archivos individuales mayores de 10 MB pueden atascarse; estos dos dashboards superan ligeramente ese umbral. Por eso se recomienda Git o CLI para este caso.

Después del despliegue, comprobar con HTTP 200 la portada y ambos dashboards en la URL real asignada, y abrir los gráficos en un navegador. No se debe informar una URL pública hasta completar esa verificación.

## Direcciones, volumen y acceso

| Necesidad | Opción para este proyecto |
| --- | --- |
| Dirección cualquiera | Netlify asigna por defecto un subdominio `nombre.netlify.app`. Se puede compartir directamente; el nombre debe estar disponible. |
| Dirección específica o empresarial | Comprar o usar un dominio propio, por ejemplo `reportes.empresa.com`, añadirlo al proyecto y configurar sus registros DNS. Netlify puede gestionar DNS o se puede mantener el proveedor DNS externo. |
| Mucha información | Los HTML estáticos funcionan, pero tamaño, cantidad de archivos y tráfico afectan la subida, el tiempo de carga y el consumo de ancho de banda. El conjunto actual suma 28,9 MB. Para datos grandes o actualizados a menudo, conviene cargar los datos mediante una API, base de datos o almacenamiento externo, y dejar los reportes livianos. Netlify no reemplaza un almacén analítico. |
| Usuarios específicos o credenciales | La visibilidad pública no controla usuarios. Para un grupo pequeño se puede usar contraseña compartida del proyecto, según el plan; para identificar personas y conceder acceso por rol se necesita autenticación y autorización, por ejemplo Netlify Identity o un proveedor externo con JWT y reglas de acceso. Los archivos que deban permanecer privados no deben exponerse como recursos públicos del sitio. |

## Dos características de pago aplicables

1. **Analítica web de Pro:** permite consultar hasta 30 días de visitas. Serviría para medir qué dashboard usan más los lectores y orientar mejoras.
2. **Colaboración de Pro:** permite miembros de equipo con roles y flujos de revisión. Serviría para que analistas revisen cambios de los reportes antes de publicarlos.

Las condiciones y límites pueden cambiar; consultar la documentación vigente antes de contratar.

## Fuentes oficiales

- [Netlify Drop y sus límites prácticos](https://docs.netlify.com/start/quickstarts/netlify-drop-quickstart/)
- [Agregar un proyecto](https://docs.netlify.com/manage/projects/add-new-project/)
- [Dominios de Netlify](https://docs.netlify.com/manage/domains/domains-fundamentals/understand-domains/)
- [Configurar un dominio propio](https://docs.netlify.com/manage/domains/get-started-with-domains/)
- [Créditos y ancho de banda](https://docs.netlify.com/manage/accounts-and-billing/billing/billing-for-credit-based-plans/how-credits-work/)
- [Opciones de acceso](https://docs.netlify.com/manage/security/secure-access-to-sites/overview/)
- [Planes y funciones Pro](https://docs.netlify.com/manage/accounts-and-billing/billing/billing-for-credit-based-plans/credit-based-pricing-plans/)
