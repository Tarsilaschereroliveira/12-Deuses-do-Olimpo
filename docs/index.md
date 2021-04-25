## Welcome a pagina Os 12 Deuses

Nela você vai aprender sobre todos os 12 deuses do olimpo 

using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace MenuTransparencia
{
    class Program
    {
        static void Main(string[] args)
        {
            var menus = Banco.ListarTodos();

            MostraMenu(menus.OrderBy(x => x.Titulo));
        }

        public static void MostraMenu(IEnumerable<MenuTransparencia> menus, int nivel = 0)
        {
            foreach (var menu in menus)
            {
                var tabs = new String('\t', nivel);

                Console.WriteLine("{0} {1}", tabs, menu.Titulo);

                if (menu.MenusTransparencia.Any())
                {
                    nivel++;
                    MostraMenu(menu.MenusTransparencia, nivel);
                    nivel--;
                }

            }
        }
    }


    public class Banco
    {
        public static IEnumerable<MenuTransparencia> ListarTodos()
        {
            return new List<MenuTransparencia>()
                       {
                           new MenuTransparencia()
                               {
                                   Titulo = "Menu Nivel 1",
                                   Link = "~/Nivel_1",
                                   MenusTransparencia = new List<MenuTransparencia>()
                                                            {
                                                                new MenuTransparencia()
                                                                    {
                                                                        Titulo = "Menu Nivel2",
                                                                        Link = "~/Nivel_2",
                                                                        MenusTransparencia = new List<MenuTransparencia>()
                                                                                                    {
                                                                                                        new MenuTransparencia()
                                                                                                            {
                                                                                                                Titulo = "Menu Nivel3",
                                                                                                                Link = "~/Nivel_3"
                                                                                                            },
                                                                                                        new MenuTransparencia()
                                                                                                            {
                                                                                                                Titulo = "Menu Nivel3",
                                                                                                                Link = "~/Nivel_3"
                                                                                                            }
                                                                                                    }
                                                                    },
                                                                new MenuTransparencia()
                                                                    {
                                                                        Titulo = "Menu Nivel2",
                                                                        Link = "~/Nivel_2"
                                                                    }
                                                            }
                               },
                               new MenuTransparencia()
                               {
                                   Titulo = "Menu Nivel1",
                                   Link = "~/Nivel_1",
                                   MenusTransparencia = new List<MenuTransparencia>()
                                                            {
                                                                new MenuTransparencia()
                                                                    {
                                                                        Titulo = "Menu Nivel2",
                                                                        Link = "~/Nivel_2"
                                                                    },
                                                                new MenuTransparencia()
                                                                    {
                                                                        Titulo = "Menu Nivel2",
                                                                        Link = "~/Nivel_2"
                                                                    }
                                                            }
                               },
                               new MenuTransparencia()
                               {
                                   Titulo = "Menu Nivel1",
                                   Link = "~/Nivel_1"
                               },
                               new MenuTransparencia()
                               {
                                   Titulo = "Menu Nivel1",
                                   Link = "~/Nivel_1"
                               },

                       };
        }
    }

    public class MenuTransparencia
    {
        public MenuTransparencia()
        {
            MenusTransparencia = new List<MenuTransparencia>();
        }
        public string Titulo { get; set; }
        public string Link { get; set; }
        public IEnumerable<MenuTransparencia> MenusTransparencia { get; set; }
    }
}
