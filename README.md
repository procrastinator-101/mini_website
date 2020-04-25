**welcome to this website**

`
#include <iostream>
#include <vector>
#include <algorithm>
#include <float.h>

#define END(X) (X < n - 1 ? X + 1 : 0)

using namespace std;

int main()
{
    int t, i, n, h, d, r, k;

    cin >> t;
    while (t--)
    {
        cin >> n;
        vector <int> a, b;
        vector <float> s;
        r = 0;
        for (i = 0; i < n; i++)
        {
            cin >> h >> d;
            a.push_back(h);
            b.push_back(d);
            s.push_back((float)b[i] / (float)a[i] - a[i]);
        }
        while (1)
        {
            k = max_element(s.begin(), s.end()) - s.begin();
            for (i = 0; i < n; i++)
                cout << s[i] << '\t';
            cout << k << endl;
            if (s[k] == -FLT_MAX)
                break ;
            r += a[k];
            a[k] = 0;
            s[k] = -FLT_MAX;
            while (a[END(k)] > 0)
            {
                a[END(k)] -= b[k];
                k = END(k);
                s[k] = a[k] < 0 ? -FLT_MAX : (float)b[k] / (float)a[k] - a[k];
                if (a[k] > 0)
                    break ;
            }
        }
        cout << r << endl;
    }
}`

please visit https://towardsdatascience.com/how-to-create-a-free-github-pages-website-53743d7524e1 for more info.
