git clone https://github.com/вашето-потребителско-име/вашето-хранилище.git
cd вашето-хранилище

git checkout -b singleton

public sealed class Logger
{
    private static Logger instance;
    private List<string> logMessages;

    private Logger()
    {
        logMessages = new List<string>();
    }

    public static Logger Instance
    {
        get
        {
            if (instance == null)
            {
                instance = new Logger();
            }
            return instance;
        }
    }

    public void Log(string message)
    {
        logMessages.Add(message);
        Console.WriteLine($"Logged: {message}");
    }

    public void PrintLogs()
    {
        Console.WriteLine("Log Messages:");
        foreach (var msg in logMessages)
        {
            Console.WriteLine(msg);
        }
    }
}

public interface IProgram
{
    void Log(string message);
}

git checkout -b prototype

using System;

public class DB : ICloneable
{
    private string connectionString;

    public DB(string connectionString)
    {
        this.connectionString = connectionString;
    }

    public void Connect()
    {
        Console.WriteLine($"Connected to Database: {connectionString}");
    }

    public object Clone()
    {
        // Shallow copy
        return this.MemberwiseClone();
    }
}

git checkout master
git merge singleton
git merge prototype

git add .
git commit -m "Merge singleton and prototype branches"

git push origin master
