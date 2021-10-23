def num(p, q):
    outp = []
    iter = [1 for i in range(p)]
    outp.append((iter.copy()))
    while iter != [q for i in range(p)]:
        for i in range(p):
            if iter[i] < p:
                iter[i] += 1
                break
            else:
                iter[i] = 1
                continue
        outp.append(iter.copy())
        continue
    return outp


def E_delta(n):
    outp = [[0 for j in range(n)] for i in range(n)]
    for i in range(n):
        outp[i][i] = "delta"
        continue
    return outp


def delta(x, y):
    if x == y:
        return 1
    else:
        return 0


def mul(A, E, B):
    outp = [[0 for j in range(len(B[0]))] for i in range(len(A))]
    for i in range(len(A)):
        for l in range(len(B[0])):
            for j in range(len(E)):
                for k in range(len(E[0])):
                    if E[j][k] == "delta":
                        outp[i][l] += delta(A[i][j], B[k][l])
                        continue
                    else:
                        continue
    return outp


def tsp(inp):
    outp = [[0 for j in range(len(inp))] for i in range(len(inp[0]))]
    for i in range(len(inp)):
        for j in range(len(inp[0])):
            outp[j][i] = inp[i][j]
    return outp


def fact(inp):
    if inp == 0:
        return 1
    else:
        return inp * fact(inp - 1)


def perm(inp):
    outp = []
    if len(inp) == 1:
        outp += [inp]
        return outp
    else:
        for i in range(len(inp)):
            for j in range(fact(len(inp) - 1)):
                outp.append([inp[i]] + perm(inp[: i] + inp[i+1:])[j])
        return outp


def max_C(inp):
    outp = []
    for i in tsp(inp):
        outp.append(max(i))
    return outp


def its(x, y):
    outp = []
    for i in x:
        if i in y:
            outp.append(i)
    return outp


def uni(x, y):
    outp = []
    for i in x + y:
        if i not in outp:
            outp.append(i)
    return outp


def solve():
    p = int(input("请输入位置数量："))
    q = int(input("请输入图案数量："))
    A = tsp(num(p, q))
    R = num(p, q)
    times = 1
    while True:
        print("第" + str(times) + "次迭代")
        I = []
        O_1 = []
        O_2 = []
        for i in range(p):
            I.append([int(input("第 " + str(i + 1) + " 次输入："))])
        O_1.append([int(input("第 1 类输出："))])
        O_2.append([int(input("第 2 类输出："))])
        opt_1 = []
        arg_1 = mul(tsp(O_1), E_delta(1), mul(tsp(I), E_delta(p), A))
        for i in range(p ** q):
            if arg_1[0][i] == 1:
                opt_1.append(tsp(A)[i])
        opt_2 = []
        arg_2 = mul(tsp(O_2), E_delta(1), [max_C(mul(perm(tsp(I)[0]), E_delta(p), A))])
        for i in range(p ** q):
            if arg_2[0][i] == 1:
                opt_2.append(tsp(A)[i])
        R = its(R, its(opt_1, opt_2))
        if len(R) != 1:
            print("当前结果集合为：")
            print(R)
            print("__________")
            times += 1
        else:
            print("最终结果集合为：")
            print(R[0])
            print("__________")
            break
    return


solve()
