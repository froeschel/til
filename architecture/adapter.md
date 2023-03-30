# Adapter Pattern

The Adapter pattern acts as a connector between two incompatible interfaces. This way it becomes possible to convert an interface to another interface that the client expects. A real life example of this could be when we a building a weather app and we need to get tempatures from different provideres. They all have the capability to return temperatures, but the methods and maybe also the format of the return value will be different. So one provider uses a method called ``GetTemperatureForLocation`` which returns a double and another provider uses a method called ``GetTemperatureForArea`` which returns a string. Code could look like this:

``
 
     public interface IWeatherService
        { 
            double GetTemperatureForCity(string city);
        }

        public interface ISourceWeatherServiceOne 
        {
            double GetTemperatureForLocation(string city);
        }

        public interface ISourceWeatherServiceTwo
        {
            string GetTemperatureForArea(string city);
        }

        public class SourceWeatherServiceOne : ISourceWeatherServiceOne
        {
            public double GetTemperatureForLocation(string city)
            {
                return 1.5;
            }
        }

        public class SourceWeatherServiceTwo : ISourceWeatherServiceTwo
        {
            public string GetTemperatureForArea(string city)
            {
                return "10";
            }
        }

        public class WeatherServicOneAdapter : IWeatherService
        {
            private readonly ISourceWeatherServiceOne _sourceWeatherServiceOne;

            public WeatherServicOneAdapter(ISourceWeatherServiceOne sourceWeatherServiceOne)
            {
                _sourceWeatherServiceOne = sourceWeatherServiceOne;
            }

            public double GetTemperatureForCity(string city)
            {
                return _sourceWeatherServiceOne.GetTemperatureForLocation(city);
            }
        }


        public class WeatherServicTwoAdapter : IWeatherService
        {
            private readonly ISourceWeatherServiceTwo _sourceWeatherServiceTwo;

            public WeatherServicTwoAdapter(ISourceWeatherServiceTwo sourceWeatherServiceTwo)
            {
                _sourceWeatherServiceTwo = sourceWeatherServiceTwo;
            }

            public double GetTemperatureForCity(string city)
            {
                return double.Parse(_sourceWeatherServiceTwo.GetTemperatureForArea(city));
            }
        }

``