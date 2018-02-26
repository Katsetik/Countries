# Countries

using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using ConsoleApplication2.Countries;

namespace ConsoleApplication2.Countries
{
    public abstract class Country : Icountry
    {
        public virtual Currency Currency { get { return Currency.EUR; } }
        public abstract string Name { get; }
    }
}

using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using ConsoleApplication2.Countries;

namespace ConsoleApplication2.Countries
{
    public class England : Country
    {
        public override string Name
        {

            get
            {
                return "England";
            }
        }
        public override Currency Currency
        {
            get
            {
                return Currency.GBP;
            }
        }
    }
}

using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using ConsoleApplication2.Countries;

namespace ConsoleApplication2.Countries
{
    public class France : Country
    {
        public override string Name
        {

            get
            {
                return "France";
            }
        }
        public override Currency Currency
        {
            get
            {
                return Currency.EUR;
            }
        }
    }
}

using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using ConsoleApplication2.Countries;

namespace ConsoleApplication2.Countries
{
    public class Germany : Country
    {
        public override string Name
        {

            get
            {
                return "Germany";
            }
        }
        public override Currency Currency
        {
            get
            {
                return Currency.EUR;
            }
        }
    }
}

using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using ConsoleApplication2.Countries;

namespace ConsoleApplication2.Countries
{
    public interface Icountry 
    {
        string Name { get; }
        Currency Currency { get; }
    }
}

using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using ConsoleApplication2.Countries;

namespace ConsoleApplication2.Countries
{
    public class Spain : Country
    {
        public override string Name
        {

            get
            {
                return "Spain";
            }
        }
        public override Currency Currency
        {
            get
            {
                return Currency.EUR;
            }
        }
    }
}

using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using ConsoleApplication2.Countries;

namespace ConsoleApplication2.Countries
{
    public class Spain : Country
    {
        public override string Name
        {

            get
            {
                return "Spain";
            }
        }
        public override Currency Currency
        {
            get
            {
                return Currency.EUR;
            }
        }
    }
}

using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using ConsoleApplication2.Countries;

namespace ConsoleApplication2.Countries
{
    public class Ukraine : Country
    {
        public override string Name
        {

            get
            {
                return "Ukraine";
            }       
        }
        public override Currency Currency
        {
            get
            {
                return Currency.UAH;
            }
        }
    }
}

using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using ConsoleApplication2.Countries;

namespace ConsoleApplication2
{
   public enum Currency
    {
        EUR,
        UAH,
        GBP
    }
}
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using ConsoleApplication2.Countries;

namespace ConsoleApplication2
{
    public static class M
    {
        private const int CurrencyCount = 2; 
        private static readonly Currency[] _availableCCurrency =
                    new Currency[CurrencyCount];

        static M ()
        {
            _availableCCurrency[0] = Currency.UAH;
            _availableCCurrency[1] = Currency.EUR;

        }

        public static bool HasCurrency(Currency currency)
        {
            for (int i = 0; i < CurrencyCount; i++)
            {
                if (_availableCCurrency[i] == currency)
                {
                    return true;
                }
            }
            return false;
        }
    }
}

using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using ConsoleApplication2.Countries;

namespace ConsoleApplication2
{
    public static class Portal
    {
        private const int CountriesCount = 5;
        private static readonly Country[] _countries = new Country[CountriesCount];

        static Portal()
        {
            _countries[0] = new England();
            _countries[1] = new France();
            _countries[2] = new Germany();
            _countries[3] = new Spain();
            _countries[4] = new Ukraine();
        }

        public static Icountry Work()
        {
            var random = new Random();
            return _countries[random.Next(CountriesCount - 1)];
        }
    }
}


using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using ConsoleApplication2.Countries;

namespace ConsoleApplication2
{
    class Program
    {
        static void Main(string[] args)
        {
            while (true)
            {
                Console.ReadLine();
                Icountry country = Portal.Work();
                Console.WriteLine("You are in country {0}", country.Name);
                if (!M.HasCurrency (country.Currency))
                {
                    Console.WriteLine("No such currency. Go to the currency exchange");
                }
            }
        }
    }
}
